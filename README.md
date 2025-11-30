<!doctype html>
<html lang="ko">
<head>
  <meta charset="utf-8" />
  <meta name="viewport" content="width=device-width,initial-scale=1" />
  <title>Linux Process Commands Guide — README</title>
  <style>
    :root{
      --bg:#0f1724; --card:#0b1220; --muted:#9aa4b2; --accent:#60a5fa;
      --code-bg:#0b1226; --border:rgba(255,255,255,0.06);
      font-family: Inter, "Noto Sans KR", system-ui, -apple-system, "Segoe UI", Roboto, "Helvetica Neue", Arial;
    }
    html,body{height:100%}
    body{
      margin:0; background:linear-gradient(180deg,#071428 0%, #071a2a 60%);
      color:#e6eef8; -webkit-font-smoothing:antialiased; line-height:1.6;
      padding:36px;
    }
    .container{max-width:960px; margin:0 auto;}
    header{display:flex;align-items:center;gap:16px;margin-bottom:20px}
    .logo{
      width:64px;height:64px;border-radius:12px;flex:0 0 64px;
      background:linear-gradient(135deg,var(--accent),#7dd3fc);
      display:flex;align-items:center;justify-content:center;color:#04263b;font-weight:700;font-size:20px;
      box-shadow:0 6px 18px rgba(2,6,23,0.6);
    }
    h1{margin:0;font-size:1.6rem}
    p.lead{margin:6px 0 0;color:var(--muted)}
    .card{background:linear-gradient(180deg, rgba(255,255,255,0.02), rgba(255,255,255,0.01)); border:1px solid var(--border); padding:20px; border-radius:12px; box-shadow:0 8px 30px rgba(2,6,23,0.6); margin-bottom:18px}
    nav.toc{display:flex;gap:12px;flex-wrap:wrap;margin-bottom:12px}
    nav.toc a{color:var(--accent); text-decoration:none; padding:6px 10px; background:rgba(96,165,250,0.06); border-radius:8px; font-size:14px}
    h2{margin-top:18px;color:#dff1ff}
    pre{background:var(--code-bg); padding:14px; border-radius:8px; overflow:auto; border:1px solid rgba(255,255,255,0.03); font-family: ui-monospace, SFMono-Regular, Menlo, Monaco, "Roboto Mono", "Noto Sans Mono", monospace; font-size:13px}
    code.inline{background:rgba(255,255,255,0.03); padding:2px 6px; border-radius:6px; font-size:0.95em}
    table{width:100%; border-collapse:collapse; margin-top:10px}
    table th, table td{padding:8px 10px; text-align:left; border-bottom:1px dashed rgba(255,255,255,0.03); font-size:14px}
    .muted{color:var(--muted); font-size:13px}
    .example{background:linear-gradient(180deg, rgba(255,255,255,0.01), rgba(255,255,255,0.006)); padding:12px; border-radius:8px; margin-top:10px; border:1px solid rgba(255,255,255,0.02)}
    footer{margin-top:22px;color:var(--muted); font-size:13px; text-align:center}
    @media (max-width:640px){
      body{padding:18px}
      header{flex-direction:column;align-items:flex-start;gap:8px}
      .logo{width:56px;height:56px}
    }
  </style>
</head>
<body>
  <div class="container">
    <header>
      <div class="logo">LS</div>
      <div>
        <h1>Linux Process Commands Guide</h1>
        <p class="lead">`top`, `ps`, `jobs`, `kill` 명령어 정리 — 실습/숙지용 README (HTML)</p>
      </div>
    </header>

    <div class="card">
      <nav class="toc" aria-label="Table of contents">
        <a href="#top">1. top</a>
        <a href="#ps">2. ps</a>
        <a href="#jobs">3. jobs</a>
        <a href="#kill">4. kill</a>
        <a href="#examples">예제 시나리오</a>
      </nav>

      <section id="top">
        <h2>1. <code class="inline">top</code> — 프로세스 모니터링</h2>
        <p class="muted">실시간으로 시스템 상태(CPU, 메모리, 프로세스 등)를 확인합니다.</p>
        <pre><code>$ top</code></pre>

        <h4>주요 단축키</h4>
        <table>
          <thead>
            <tr><th>키</th><th>기능</th></tr>
          </thead>
          <tbody>
            <tr><td><code>q</code></td><td>top 종료</td></tr>
            <tr><td><code>k</code></td><td>프로세스 종료 (PID 입력)</td></tr>
            <tr><td><code>h</code></td><td>도움말</td></tr>
            <tr><td><code>M</code></td><td>메모리 사용량 기준 정렬</td></tr>
            <tr><td><code>P</code></td><td>CPU 사용률 기준 정렬</td></tr>
          </tbody>
        </table>

        <p class="muted">요약: 서버 모니터링 시 가장 자주 쓰는 명령어. 실시간 정보 제공.</p>
      </section>

      <section id="ps">
        <h2>2. <code class="inline">ps</code> — 프로세스 조회</h2>
        <p class="muted">현재 실행 중인 프로세스의 스냅샷을 보여줍니다.</p>

        <pre><code>
# 기본
$ ps

# 자주 쓰는 옵션
$ ps -e        # 모든 프로세스
$ ps aux       # 전체 목록 (사용자·CPU·메모리 정보 포함)
$ ps -ef       # full-format 출력
        </code></pre>

        <h4>옵션 설명</h4>
        <table>
          <thead><tr><th>옵션</th><th>설명</th></tr></thead>
          <tbody>
            <tr><td><code>a</code></td><td>터미널에 종속되지 않은 모든 프로세스</td></tr>
            <tr><td><code>u</code></td><td>사용자 정보 표시</td></tr>
            <tr><td><code>x</code></td><td>로그인 없이 실행된 프로세스 포함</td></tr>
            <tr><td><code>-ef</code></td><td>full-format 출력</td></tr>
          </tbody>
        </table>

        <p class="muted">요약: 특정 프로세스를 찾거나 스냅샷 형태의 정보를 원할 때 유용.</p>
      </section>

      <section id="jobs">
        <h2>3. <code class="inline">jobs</code> — 백그라운드 작업 확인</h2>
        <p class="muted">현재 터미널 세션에서 실행 중인 백그라운드 작업 목록을 출력합니다.</p>

        <pre><code>$ jobs</code></pre>

        <h4>상태 종류</h4>
        <table>
          <thead><tr><th>상태</th><th>의미</th></tr></thead>
          <tbody>
            <tr><td>Running</td><td>실행 중</td></tr>
            <tr><td>Stopped</td><td>일시 정지</td></tr>
            <tr><td>Done</td><td>완료</td></tr>
          </tbody>
        </table>

        <h4>관련 명령어</h4>
        <pre><code>
Ctrl + Z      # 현재 작업 중지 (SIGTSTP)
$ bg          # 백그라운드에서 재개
$ fg %1       # 작업 번호 1번을 포그라운드로 가져오기
        </code></pre>
      </section>

      <section id="kill">
        <h2>4. <code class="inline">kill</code> — 프로세스 종료</h2>
        <p class="muted">프로세스에 시그널을 보내 종료하거나 제어합니다.</p>

        <pre><code>
# 기본
$ kill <PID>

# 시그널 지정
$ kill -15 <PID>   # SIGTERM (정상 종료, 기본)
$ kill -9  <PID>   # SIGKILL (강제 종료)
        </code></pre>

        <h4>자주 쓰는 시그널</h4>
        <table>
          <thead><tr><th>시그널</th><th>번호</th><th>설명</th></tr></thead>
          <tbody>
            <tr><td>SIGTERM</td><td>15</td><td>정상 종료 요청</td></tr>
            <tr><td>SIGKILL</td><td>9</td><td>강제 종료 (회수 불가)</td></tr>
            <tr><td>SIGSTOP</td><td>19</td><td>프로세스 일시 정지</td></tr>
            <tr><td>SIGCONT</td><td>18</td><td>중지된 프로세스 재개</td></tr>
          </tbody>
        </table>
      </section>

      <section id="examples">
        <h2>예제 시나리오</h2>

        <div class="example">
          <h4>1) CPU 많이 사용하는 프로세스 찾고 종료하기</h4>
          <pre><code>
$ top            # 실행 -> 정렬(P)로 CPU 많은 것 확인
# PID 확인 후
$ kill -9 <PID>  # 강제 종료 (필요 시)
          </code></pre>
        </div>

        <div class="example">
          <h4>2) 특정 프로그램 프로세스만 찾기</h4>
          <pre><code>$ ps aux | grep python</code></pre>
        </div>

        <div class="example">
          <h4>3) 백그라운드 작업 실행 및 제어</h4>
          <pre><code>
$ python3 script.py &   # 백그라운드 실행
$ jobs                  # 작업 목록 확인
$ kill %1               # 첫 번째 job 종료 (job 제어)
          </code></pre>
        </div>
      </section>
    </div>

    <footer>
      도움 필요하면 <strong>간단한 예제 스크립트</strong>이나 <strong>PDF/마크다운 출력용 버전</strong>으로도 만들어 드릴게요.
    </footer>
  </div>
</body>
</html>
