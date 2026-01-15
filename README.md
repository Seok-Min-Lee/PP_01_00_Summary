# 비하인더씬(Behind The Scene)
### 개요
**웹캠과 Google MediaPipe 기반 얼굴 인식**을 활용하여 실시간 이미지 합성합니다.</br>
체험자는 **촬영 → 편집 → 전시**의 순서를 따라 이동하며 체험합니다. </br>
각 단계는 각 단계는 물리적으로 다른 공간과 장비에서 수행되며,
이를 하나의 체험 세션으로 연결하기 위해 **TCP 기반 중앙 서버가 모든 상태와 데이터를 중계**합니다.</br>
여러 대의 키오스크와 디스플레이가 하나의 체험 흐름으로 동작하는 **분산형 인터랙티브 전시 시스템**입니다.
</br>

### 프로그램 4종
<table>
  <tr>
    <td align="center" width="150">
      구분
    </td>
    <td align="center" width="850">
      역할 및 Git Repository
    </td>
  </tr>
  
  <tr>
    <td align="center" width="150" rowspan="2">
      Studio(촬영)
    </td>
    <td width="850">
      웹캠으로 촬영한 원본 이미지를 서버에 업로드
    </td>
  </tr>
  <tr>
    <td width="850">
      https://github.com/Seok-Min-Lee/PP_01_01_Studio
    </td>
  </tr>
  
  <tr>
    <td align="center" width="150" rowspan="2">
      Editor(편집)
    </td>
    <td width="850">
      고유 비밀번호를 입력하여 이미지를 불러오고 얼굴을 인식하여 마스크 및 필터 적용, 다운로드 QR링크 제공
    </td>
  </tr>
  <tr>
    <td width="850">
      https://github.com/Seok-Min-Lee/PP_01_02_Editor
    </td>
  </tr>
  
  <tr>
    <td align="center" width="150" rowspan="2">
      Gallery(전시)
    </td>
    <td width="850">
      서버로부터 편집 완료된 이미지를 받아 실시간 전시
    </td>
  </tr>
  <tr>
    <td width="850">
      https://github.com/Seok-Min-Lee/PP_01_03_Gallery
    </td>
  </tr>
  
  <tr>
    <td align="center" width="150" rowspan="2">
      Server
    </td>
    <td width="850">
      세션 관리, 이미지 저장, 클라이언트 간 데이터 라우팅
    </td>
  </tr>
  <tr>
    <td width="850">
      https://github.com/Seok-Min-Lee/PP_01_04_Server
    </td>
  </tr>
</table>
</br>


### 사용 기술
├─ 실시간 얼굴 인식 (MediaPipe) - Studio, Editor </br>
├─ 이미지 합성 및 포스트 프로세싱 - Editor </br>
├─ TCP 기반 이진 이미지 전송 - Server </br>
└─ 세션 기반 멀티 클라이언트 라우팅 - Server </br>
</br>

### 데모 시연 영상
*실제 운영중인 버전의 리소스와 일부 기능을 덜어내고 데모버전으로 재개발하였습니다.</br>
https://www.youtube.com/watch?v=G9FG8mV-jX0
</br></br>

## 체험 플로우
![체험 플로우](behindthescene_zone_drawing.png)
<table>
  <tr>
    <td align="center" width="100">순서</td>
    <td align="center" width="900">내용</td>
  </tr>

  <tr>
    <td align="center">1</td>
    <td>체험자가 Studio에서 사진 촬영</td>
  </tr>
  <tr>
    <td align="center">2</td>
    <td>Studio는 사진을 서버에 업로드하고 세션 코드(고유 비밀번호)를 생성받음</td>
  </tr>
  <tr>
    <td align="center">3</td>
    <td>체험자가 Editor로 이동하여 세션 코드를 입력</td>
  </tr>
  <tr>
    <td align="center">4</td>
    <td>서버가 세션 코드에 매핑된 이미지를 조회하여 해당 Editor로 라우팅</td>
  </tr>
  <tr>
    <td align="center">5</td>
    <td>체험자가 적용할 마스크/필터를 선택</td>
  </tr>
  <tr>
    <td align="center">6</td>
    <td>Editor는 마스크/필터를 적용하고 결과를 서버에 업로드</td>
  </tr>
  <tr>
    <td align="center">7</td>
    <td>Gallery가 해당 이미지를 받아 실시간 전시</td>
  </tr>
</table>
</br>

## 시스템 구성
![시스템 구성](behindthescene_system_drawing.png)
</br>

## 최종 결과물
![최종 결과물](behindthescene_result_example.png)
</br>
