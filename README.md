# 🐥 SSAFY 공통 프로젝트
<img src="https://img.shields.io/badge/results-Responsive WebApp-blue">
<img src="https://img.shields.io/badge/framework-Vue.js 2.0-green">
<img src="https://img.shields.io/badge/framework-Spring Boot-green">
<img src="https://img.shields.io/badge/DataBase-MySQL-green">
<img src="https://img.shields.io/badge/version-v1.0.0-red">
<br>

## Core Team  😜

<table>
   <tr>
      <td>
        <img width="160px" src="https://lab.ssafy.com/webmobile1-sub1/s02p11d138/raw/develop/KakaoTalk_20200109_090135135.jpg"><br>
         [홍성욱](https://github.com/Woogie924)<br>
         <i>Project lead & Developer</i><br>
         <i>SSAFY 2기 교육생</i>
      </td>
      <td>
        <img width="160px" src="https://lab.ssafy.com/webmobile1-sub1/s02p11d138/raw/develop/Profile/%EC%9D%B4%EC%9D%91%EC%9E%AC.jpg"><br>
         [이응재](https://github.com/Woogie924)<br>
         <i>Project lead & Developer</i><br>
         <i>SSAFY 2기 교육생</i>
      </td>
      <td>
        <img width="160px" src="https://lab.ssafy.com/webmobile1-sub1/s02p11d138/raw/develop/Profile/%EA%B9%80%ED%98%84%EC%9A%B0.jpg"><br>
         [김현우](https://github.com/Woogie924)<br>
         <i>Project lead & Developer</i><br>
         <i>SSAFY 2기 교육생</i>
      </td>
      <td>
        <img width="160px" src="https://lab.ssafy.com/webmobile1-sub1/s02p11d138/raw/develop/Profile/%EB%B0%95%EA%B5%90%EC%97%B4.jpg"><br>
         [박교열](https://github.com/Woogie924)<br>
         <i>Project lead & Developer</i><br>
         <i>SSAFY 2기 교육생</i>
      </td>
      <td>
        <img width="160px" src="https://lab.ssafy.com/webmobile1-sub1/s02p11d138/raw/develop/Profile/%EA%B9%80%EC%A0%95%EB%8D%95.jpg"><br>
         [김정덕](https://github.com/Woogie924)<br>
         <i>Project lead & Developer</i><br>
         <i>SSAFY 2기 교육생</i>
      </td>
   </tr>
</table>


### Overview
---
해당 프로젝트는 Firebase, Node.js, Vue.js기반으로 반응형 웹 서비스를 제공합니다.  
Gitlab과 연동하여서 자신이 만들어놓은 프로젝트들의 목록을 확인할 수 있습니다.  
Firebase를 사용하여 해당 웹 페이지를 배포해서 사용하는 사용자의 사용기기 사이즈에 맞게 반응형 웹 서비스를 제공함으로서 사용자들은 좀 더 편리하게 웹 서비스를 이용할 수 있습니다.  

### Setup
---
사용하기 전에 다음 조건을 모두 설치했는지 확인하십시오.
* Node.js - Download & Install Node.js and the npm package manager. 

> npm install  
> npm install -g yarn  
> npm install -g @vue/cli  
> npm install vue  
> npm install -g firebase tools  

설치 후 제대로 설치가 되었는지 확인하세요.
> npm list


### Build
---
* 자신의 파이어베이스로 배포를 하고 싶다면 파이어베이스 프로젝트를 만들고 FirebaseService.j 파일에 자신의 프로젝트 ID와 기타 설정값들을 변경해주시길 바랍니다. 
* 자신의 GitLab의 프로젝트 정보들을 보고싶다면 GitlabService.js 파일에 있는 메소드에 들어가는 변수 값들을 자신의 Gitlab ID에 맞게 설정해주시길 바랍니다.

### Test
---
local영역에서 자신이 수정한 결과를 확인하고 싶다면 해당 뷰 프로젝트 경로에서 

> npm run serve  

서버를 가동하고 하단에 "App Running"메세지를 확인하고 http://localhost:8080/ 으로 접속하면 프로젝트 실행 화면을 확인할 수 있습니다.

### Run
---
현재 버전이 https://sub-pjt-1-1ce19.firebaseapp.com/ 으로 배포되고 있습니다.

### Deploy
---
해당 프로젝트를 수정해서 배포를 하고 싶다면 아래와 같이 따라하십시오.
1. Firebase 프로젝트를 생성하고 .firebaserc파일의 프로젝트id의 default값을 자신의 firebase project ID로 수정해줍니다.  
2. 해당 skeleton project 폴더의 커맨드창에서 npm run build를 실행하여 dist파일을 생성해줍니다.
3. firebase tools가 설치되어있지 않다면 설치를 하고 설치가 되어있다면 firebase login 커맨드를 치고 login을 해줍니다.
4. login이 완료 되었다면 firebase init커맨드를 실행하고 Hosting을 체크해주시고 배포할 폴더를 dist로 변경해줍니다.
5. index.html은 overwrite하지 않습니다.
6. firebase init이 완료되었다면 firebase deploy 커맨드를 실행해줍니다.
7. deploy 커맨드가 완료되면 하단에 있는 url로 접속을 확인합니다.