# API 문서

## 목차
1. [GIS건물통합WFS조회](#gis건물통합wfs조회)
2. [국토교통부_건축HUB_건축물대장정보 서비스](#국토교통부_건축hub_건축물대장정보-서비스)

## GIS건물통합WFS조회

### 기본 정보
- **API 이름**: GIS건물통합WFS조회
- **설명**: 좌표 데이터를 기반으로 건물 정보를 조회하는 WFS(Web Feature Service) API
- **데이터 타입**: dt_d010
- **API 문서 주소**: [브이월드 API 문서](https://www.vworld.kr/dtna/dtna_apiSvcFc_s001.do?pageIndex=1&searchApiGbn=&searchGrpSeq=&searchKeyword=GIS%EA%B1%B4%EB%AC%BC%ED%86%B5%ED%95%A9&apiNum=76)

### 요청 파라미터

#### 필수 파라미터
| 파라미터명 | 설명 | 타입 | 예시 |
|------------|------|------|------|
| typename | 필터링 대상인 하나 이상의 피처 타입의 피처 유형 리스트 | string | dt_d010 |
| bbox | 좌표 범위 | string | 37.5646195229392,127... |
| pnu | 필지고유번호 19자리 | string | 1174011000102450001 |
| maxFeatures | 요청에 대한 응답으로 WFS가 반환해야하는 피처의 최대 값 | integer | 10 |
| resultType | 요청에 대하여 WFS가 어떻게 응답할 것인지 정의 | string | results |
| srsName | 반환되어야 할 피처의 기하에 사용되어야 할 WFS가 지원하는 좌표체계 | string | EPSG:4326 |
| output | 요청에 대한 WFS 응답 포맷을 설정 | string | GML2 |

#### 선택 파라미터
| 파라미터명 | 설명 | 타입 | 예시 |
|------------|------|------|------|
| key | 발급받은 api key | string | - |
| domain | 요청변수 | string | - |

### 응답 필드
| 필드명 | 설명 | 타입 | 예시 |
|--------|------|------|------|
| ag_geom | 공간자료 | string | 127.20224761,37.54050649... |
| src_objectid | 원천도형ID | string | 161643 |
| gis_idntfc_no | GIS건물통합식별번호 | string | 198420116029452727560000000 |
| pnu | 고유번호 | string | 1111011000101250000 |
| ld_cpsg_code | 법정동 시도시군 코드 | string | 11110 |
| mnnm | 본번 | string | 0023 |
| slno | 부번 | string | 0015 |
| regstr_se_code | 특수지코드 | string | 1 |
| buld_prpos_code | 건축물용도코드 | string | 01000 |
| strct_code | 건축물구조코드 | string | 11 |
| ar | 건축물면적(㎡) | number | 0 |
| use_confm_de | 사용승인일자 | string | 19840625 |
| totar | 연면적(㎡) | number | 177.08 |
| plot_ar | 대지면적(㎡) | number | 0 |
| hg | 높이(m) | number | 0 |
| btl_rt | 건폐율(%) | number | 0 |
| measrmt_rt | 용적율(%) | number | 0 |
| buld_idntfc_no | 건축물ID | string | 1903 |
| violt_bild | 위반건축물여부 | string | 0 |
| refrn_systm_cntc_no | 참조체계연계키 | string | B00100000000T37HX |
| last_updt_dt | 데이터기준일자 | datetime | 2015-11-18T13:19:59 |

### 에러 코드
| 코드 | 레벨 | 메시지 | 설명 |
|------|------|---------|------|
| URL_TYPE | 1 | 잘못된 URL 입니다. | - |
| PARAM_REQUIRED | 1 | 필수 파라미터인 <%S1>가 없어서 요청을 처리할 수 없습니다. | %S1: 파라미터 이름 |
| INVALID_TYPE | 1 | <%S1> 파라미터 타입이 유효하지 않습니다.<br>유효한 파라미터 타입: <%S2><br>입력한 파라미터 값: <%S3> | %S1: 파라미터 이름<br>%S2: 유효한 파라미터 값의 유형<br>%S3: 입력한 파라미터 값 |
| INVALID_RANGE | 1 | <%S1> 파라미터의 값이 유효한 범위를 넘었습니다.<br>유효한 파라미터 타입: <%S2><br>입력한 파라미터 값: <%S3> | %S1: 파라미터 이름<br>%S2: 유효한 파라미터 값의 범위<br>%S3: 입력한 파라미터 값 |
| INVALID_KEY | 2 | 등록되지 않은 인증키입니다. | - |
| INCORRECT_KEY | 2 | 인증키 정보가 올바르지 않습니다.<br>(ex. 인증키 발급 시 입력한 도메인이 다를경우) | - |
| UNAVAILABLE_KEY | 2 | 임시로 인증키를 사용할 수 없는 상태입니다. | - |
| OVER_REQUEST_LIMIT | 2 | 서비스 사용량이 일일 제한량을 초과하여 더 이상 서비스를 사용할 수 없습니다. | - |
| SYSTEM_ERROR | 3 | 시스템 에러가 발생하였습니다. | - |
| UNKNOWN_ERROR | 3 | 알 수 없는 에러가 발생하였습니다. | - |

### 참고사항
- EPSG:4326 좌표계 사용
- 결과는 GML2 형식으로 반환
- 최대 조회 건수는 1000건으로 제한
- HTTPS, FLEX를 필수로 사용해야 하며 보안상의 이유로 API사용은 DOMAIN을 추가하여 서비스를 이용해야 함 

## 국토교통부_건축HUB_건축물대장정보 서비스

### 기본 정보
- **API 이름**: 국토교통부_건축HUB_건축물대장정보 서비스
- **설명**: 부동산 물건 관리시 해당 건물의 본인인증에 필요한 정보
- **API 문서 주소**: [공공데이터포털 API 문서](https://www.data.go.kr/iim/api/selectAPIAcountView.do)
- **엔드포인트**: http://apis.data.go.kr/1613000/BldRgstHubService
- **라이센스**: 이용허락범위 제한 없음

### 요청 파라미터

#### 필수 파라미터
| 파라미터명 | 설명 | 타입 | 예시 |
|------------|------|------|------|
| serviceKey | 공공데이터포털에서 받은 인증키 | string | 'abc123456789' |
| sigunguCd | 시군구코드 | string | '11680' |
| bjdongCd | 법정동코드 | string | '10300' |

#### 선택 파라미터
| 파라미터명 | 설명 | 타입 | 예시 |
|------------|------|------|------|
| platGbCd | 대지구분코드(0:대지 1:산 2:블록) | string | '0' |
| bun | 번 | string | '0001' |
| ji | 지 | string | '0002' |
| startDate | 검색시작일(YYYYMMDD) | string | '20240101' |
| endDate | 검색종료일(YYYYMMDD) | string | '20240331' |
| _type | 리턴 타입 (xml, json) 생략 시 xml로 기본 제공 | string | 'json' |
| numOfRows | 리스트수 | string | '10' |
| pageNo | 페이지번호 | string | '1' |

### 참고사항
- 공공데이터포털 회원가입 후 API 인증키를 발급받아야 사용 가능
- HTTPS 지원
- 일일 트래픽 제한이 있으므로 확인 필요 