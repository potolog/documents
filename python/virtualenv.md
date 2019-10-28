# virtualenv

Python 개발환경을 구축할 때 필요한 것 중 하나가 바로 virtualenv 환경을 세팅하는 것이다.

virtualenv 를 통해 다양한 python 패키지를 독립적으로 설치하여 프로젝트별로 관리할 수 있다.


### virtualenv 인스톨
<pre>
$ sudu pip3 install virtualenv
</pre>

### virtualenv 생성
<pre>
# virtualenv python_env
</pre>

### virtualenv 실행
<pre>
# source ~/python_env/bin/activate
</pre>

### virtualenv 중지
<pre>
# deactivate
</pre>

### virtualenv 에서 패키지 등록 및 삭제
(python_env) # pip install -no패키지<br>
(python_env) # pip uninstall 패키지<br>

