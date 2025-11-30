<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>오픈소스 SW개론 과제2 - top, ps, jobs, kill 명령어 정리</title>
</head>
<body>

    <h1>📝 오픈소스 SW개론 과제 2</h1>
    <p><strong>학번:</strong> 20253034<br>
    <strong>이름:</strong> 이서린</p>

    <hr>

    <h2>🔍 top / ps / jobs / kill 명령어 정리</h2>

    <h3>1. top</h3>
    <p>시스템의 프로세스 상태와 CPU·메모리 사용량을 <strong>실시간으로 모니터링</strong>하는 명령어.</p>

    <h4>✔ 주요 기능</h4>
    <ul>
        <li>CPU·메모리 사용률을 실시간으로 표시</li>
        <li>프로세스 목록을 자원 사용량 기준으로 정렬</li>
        <li>시스템 부하 및 실행 중인 프로세스 수 제공</li>
    </ul>

    <h4>✔ 사용법</h4>
    <pre><code>top</code></pre>

    <h4>✔ 주요 단축키</h4>
    <ul>
        <li><strong>q</strong> : 종료</li>
        <li><strong>k</strong> : 특정 프로세스 종료</li>
        <li><strong>M</strong> : 메모리 사용량 기준 정렬</li>
        <li><strong>P</strong> : CPU 사용량 기준 정렬</li>
    </ul>

    <h3>2. ps</h3>
    <p>현재 실행 중인 프로세스를 <strong>스냅샷 형태</strong>로 확인하는 명령어.</p>

    <h4>✔ 주요 옵션</h4>
    <ul>
        <li><code>ps aux</code> : 모든 프로세스 상세 표시</li>
        <li><code>ps -ef</code> : full format 형태로 모든 프로세스 출력</li>
        <li><code>ps -U 사용자명</code> : 특정 사용자 프로세스만 확인</li>
    </ul>

    <h4>✔ 출력 정보</h4>
    <table border="1" cellspacing="0" cellpadding="6">
        <tr>
            <th>항목</th>
            <th>설명</th>
        </tr>
        <tr>
            <td>PID</td>
            <td>프로세스 ID</td>
        </tr>
        <tr>
            <td>USER</td>
            <td>프로세스 실행 사용자</td>
        </tr>
        <tr>
            <td>%CPU</td>
            <td>CPU 사용률</td>
        </tr>
        <tr>
            <td>%MEM</td>
            <td>메모리 사용률</td>
        </tr>
        <tr>
            <td>COMMAND</td>
            <td>실행된 명령어</td>
        </tr>
    </table>

    <h3>3. jobs</h3>
    <p>현재 쉘에서 실행 중인 <strong>백그라운드 작업 상태</strong>를 확인하는 명령어.<br>
    (해당 터미널에서 실행한 작업만 확인 가능)</p>

    <h4>✔ 사용법</h4>
    <ul>
        <li><code>jobs</code> : 실행 중인 작업 출력</li>
        <li><code>jobs -l</code> : PID 포함하여 출력</li>
    </ul>

    <h4>✔ 작업 상태 종류</h4>
    <table border="1" cellspacing="0" cellpadding="6">
        <tr>
            <th>상태</th>
            <th>설명</th>
        </tr>
        <tr>
            <td>Running</td>
            <td>실행 중</td>
        </tr>
        <tr>
            <td>Stopped</td>
            <td>일시 중지됨</td>
        </tr>
        <tr>
            <td>Done</td>
            <td>작업 완료</td>
        </tr>
    </table>

    <h3>4. kill</h3>
    <p>프로세스에 특정 <strong>시그널(signal)</strong>을 보내 종료하거나 제어하는 명령어.</p>

    <h4>✔ 사용법</h4>
    <ul>
        <li><code>kill PID</code> : 정상 종료 요청</li>
        <li><code>kill -9 PID</code> : 강제 종료</li>
        <li><code>kill -15 PID</code> : 정상 종료 요청(기본값)</li>
    </ul>

    <h4>✔ 주요 시그널</h4>
    <ul>
        <li><strong>SIGTERM (15)</strong> : 정상 종료 요청</li>
        <li><strong>SIGKILL (9)</strong> : 강제 종료</li>
        <li><strong>SIGHUP (1)</strong> : 재시작(설정 파일 재로드)</li>
        <li><strong>SIGSTOP (19)</strong> : 프로세스 일시 정지</li>
    </ul>

</body>
</html>
