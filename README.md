# ERROR 1126 해결 방법

## 1. 배경

에러가 발생할 수 있는 모든 경우의 수에 관해 논한 기술 문서는 없었기 때문에 대표적	으로 해결되는 방식 이외에는 다른 방법에 관해 상상해 내기도 쉽지 않았다. 따라서 	MariaDB 및 My SQL 사용시 생겼던 가장 골치 아픈 에러였다. 

## 2. 대표적인 해결 방법

해당 에러는 찾고자하는 파일을 찾지 못할 때 발생한다. 파일이 존재한다고 가정했을 때 유추할 수 있듯 해결 방안은 2가지 방식으로 나뉜다. (기술 문서 및 해외 사례들은 파일이 존재하지 않아 설치를 통해 해결하는 경우가 대부분이다.)

1. **권한 설정**: 파일을 읽을 수 있는 권한이 제한적일 수 있다. 적절한 권한을 설정하여 파일을 읽을 수 있도록 한다. (`chown` 사용)
2. **chmod 설정**: `chmod`를 사용하여 읽기, 쓰기, 실행에 관한 설정을 사용자, 그룹 또는 기타 사용자에게 충분한 권한을 부여한다.

위 두 가지 방식을 통해 My SQL에 관한 오류는 해결되었다고 착각했다. 


파일에 관한 넉넉한 권한과 각 계층에 관해 읽기 및 쓰기 실행에 관해 넉넉히 설정해주니 에러가 해결되었기 때문이다.


하지만 MariaDB 사용중 같은 에러가 발생하였고 에러를 해결해 보려 내가 추론한 해결방식을 통해 해결해보려 했지만 해결되지 않았다.

## 3. 실제 해결 방법

사실 문제는 아주 간단하였다. 

권한이나 읽기 모드에 관한 것이 아니었다. 

MySQL, MariaDB는 버전이 오르며 보안이 강력해졌다. 

따라서 Home을 Protect하는 설정이 추가 되었다. 

그것을 false로 해주던가 Protect하지 않는 디렉터리에 파일을 추가하면 해결된다. (위치는 여러분 마다 다르겠지만 mariadb.service 에서 ProtectHome을 false로 해주면 된다. )

앞서 MySQL에 관해 오류가 해결되었다고 착각했던 이유는 보안에 해당되지 않는 디렉터리에 파일을 생성한 후 작업을 진행했기 때문이다. 


## 끝으로

나의 우매한 실수를 여러분은 겪지 않게 하기 위해 문서를 작성한다. 
