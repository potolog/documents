## CentOS 8.0 설치


<hr>>

## Development tools 설치하기

development tools 는 개발을 할 때 필요한 툴들이다.<br>
개발 뿐만 아니라 패키지를 설치할 때도 의존성 체크나 빌드를 위하여 필요할 때가 있다.<br>
이와 같은 필요성이 있을 때 설치한다.

<pre>
# dnf groupinfo "Development Tools"
# dnf group install "Development Tools"
# dnf group remove "Development Tools"
</pre>

