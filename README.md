# Linux-instruction

리눅스 기초 명령어 공부

1. date
stdout으로 년, 월, 일을 출력한다.

2. tty
$ tty
/dev/tty1
stdout으로 터미널 파일의 위치를 출력

3. ls -l -a
현재 위치한 디렉토리의 파일리스트를 출력
-l 상세옵션
-a 모든 파일(숨긴 파일 포함)
.file하면 숨긴 파일 된다.

4. touch file
크기가 0byte인 file을 생성, 만약 file이 이미 존재한다면 무시된다.

5. mkdir directory
directory만든다.

6. cd
이동

7. pwd
현재 위치 절대경로를 stdout으로 보여준다.

8. rmdir
디렉토리 삭제

9. cat
파일이나 stdin을 읽고 stdout으로 출력한다.

10. rm -r -i
파일을 삭제한다.
-r recursive로 서브디렉토리까지 모두삭제
-i 삭제할 건지 물어보고 삭제하는 옵션

11. man
man page 도움말을 보여준다.

12. more, less
1페이지 씩 끊어서 파일을 보여준다.

13. cp
디렉토리나 파일을 복사한다.

14. mv
디렉토리나 파일을 이동한다.

15. head (-줄 수) 파일, tail (- 줄 수) 파일
파일의 일부분을 보여준다.
head는 위에서부터
tail은 아래서부터
줄 수는 default 10이다.

16. grep <string> file
파일의 내용 중 string에 해당하는 부분을 찾는다.

17. od -x -a
파일의 내용을 8진수로 보여준다.
-x옵션은 16진수로 보여주는 옵션
-a옵션은 ASCII로 보여주는 옵션
옵션은 같이 써도 된다.

18. ln file1 file2 -s
file1의 링크를 file2도 이용한다. (file1 삭제 시, file2로 접근 가능)
-s 옵션 심볼릭 링크로써, file1 삭제 시, file2로도 접근 불가하다. (바로가기)
$ ln -s /tmp /var/tmp 

19. tar

$ tar cvf T.tar *
현재 디렉토리의 모든 파일을 T.tar하나로 관리 -> 압축이 아니다.
$ tar xvf T.tar
현재 디렉토리에 T.tar로 관리되던 모든 파일 풀기

20. gzip
$ gzip -9v test.txt
1~9까지 압축 강도 조정 숫자 낮을 수록 빠르지만 압축률이 가장 낮음
v 압축 하기
$ gzig -d test.gz
d 압축 풀기

21. echo <string>
string을 그대로 stdout으로 출력

22. sleep <numeric>
numeric만큼 아무동작도 안함

순차실행법 
;로 구분짓는다.
$ sleep 5; echo i wake;
백그라운드 실행법
명령어 맨 마지막에 &를 표시한다.
$ sleep 5&

23. history
이 때까지 입력했던 명령어 표시

24. jobs
현재 수행중인 작업 표시

25. fg, bg
중지된 forground작업 실행
중지된 background작업 실행
중지된 것 중 가장 최근에 중지된 것 부터 실행
fg %n n번째로 중단된 작업 실행
n을 보는 방법은 jobs명령으로 확인

26. ps
상세 작업 정보

27. kill -9
프로세스 죽이기
-9명령은 가장 강력한 신호로 죽이기

28. !! !(문자) !(history 번호)
!!는 가장 최근의 실행했던 명령 재실행
!(문자)는 (문자)로 시작하는 가장 최근의 명령 재실행
!(history 번호) 해당 번호의 명령 재실행

29. alias (symbol) = 명령
명령어의 길이가 길거나 자주사용하는 경우 명령어를 심볼로 대체

30. diff file1 file2
file1의 내용과 file2의 내용의 차이를 stdout으로 보여준다.

31. wc (file1)
file1의 줄 수, 단어 수, 바이트 수, 파일 명을 보여준다.
$ echo hello | wc
이런식으로도 사용가능하다
결과는 	1	1	6(eof까지)

32. redirection

명령 >& 파일명 : 명령이 실행된 표준 출력의 결과와 에러를 파일로 출력
명령 >>& 파일명 : 명령이 실행된 표준 출력의 결과와 에러를 파일로 덧붙여 출력
명령 > 파일명 : 파일의 존재 유무와 상관없이 생성하고 명령이 실행된 표준 출력의 결과를 파일로 출력
명령 >&! 파일명 : 파일의 존재 유무와 상관없이 생성하고 명령이 실행된 표준 출력의 결과와 에러를 파일로 출력
명령 >> 파일명 : 파일의 존재 유무와 상관없이 생성하고 파일에 덧붙여 출력
명령 >>& 파일명 : 파일의 존재 유무와 상관없이 생성하고 명령이 실행된 표준 출력의 결과와 에러를 파일에 덧붙여 출력
명령A | 명령B : 명령A의 출력을 명령B 입력으로 사용하여 실행
명령A |& 명령B : 명령A의 출력과 에러를 명령 B의 입력으로 사용하여 실행

$ head < ls.txt > ls2.txt
위의 코드는 다음과 같은 순서로 실행 됩니다.

ls.txt의 내용을 head 명령어의 입력 스트림으로 전송
head 명령어는 입력 받은 ls.txt의 내용에서 처음 10줄을 출력
head 명령어의 출력 스트림을 ls2.txt 파일에 연결
head 명령어의 출력 스트림은 콘솔이 아닌 ls2.txt에 연결 되어 있으므로 출력 결과를 ls2.txt에 저장

$ cat > hello
hello world!
ctrl + d(EOF)
$ cat hello
hello world!

32. 파이프 라인 분기
echo hello | tee file1 file2
file1, file2, stdout에 hello를 쓴다.
