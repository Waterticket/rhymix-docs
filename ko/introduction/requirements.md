설치 환경
---------

라이믹스를 설치하고 원활하게 사용하려면 아래와 같은 조건이 갖추어져야 합니다.

  - PHP 5.5.9 이상 (PHP 7.0 이상 권장)
  - MySQL 5.0.7 이상 (MariaDB 권장)
  - 필수 PHP 모듈
    - curl
    - gd
    - iconv 또는 mbstring
    - json
    - mcrypt 또는 openssl
    - simplexml

아파치 서버인 경우 mod_rewrite를 권장하나, 필수는 아닙니다.
nginx에서 rewrite를 설정하는 방법은 [여기](nginx.md)를 참고하십시오.

### 퍼미션

`files` 폴더에 쓰기 권한이 주어져야 합니다.
호스팅 환경에 따라 `files` 폴더의 퍼미션을 777 또는 707로 변경해야 할 수도 있고,
최근에는 웹서버의 PHP 실행 권한이 FTP 계정과 일치하도록 미리 세팅되어 있어
퍼미션 조정이 필요없는 경우도 있습니다.

설치 경로에 쓰기 권한이 이미 있는 경우, 설치 과정에서 `files` 폴더를 자동으로 생성합니다.

#### php.ini 설정 참고

`session.auto_start` = `off`로 설정되어 있어야 합니다.
최근 호스팅 환경에서 이 설정이 문제가 되는 경우는 거의 없습니다.

`upload_max_filesize` 설정을 통해 한 번에 업로드할 수 있는 파일 용량을 조정할 수 있습니다.
일반적으로 `upload_max_filesize`보다 `post_max_size`가 커야 하고, `post_max_size`보다 `memory_limit`이 커야 합니다.
그러나 라이믹스는 대용량 파일을 분할 업로드하는 것을 지원하므로 업로드 용량이 10M 이상 주어지기만 하면
서버 용량 내에서 사실상 무한대로 업로드가 가능합니다.

`memory_limit`은 최소 128M가 주어져야 하며, 대용량 이미지 처리가 필요한 사이트라면 256M가 필요할 수도 있습니다.