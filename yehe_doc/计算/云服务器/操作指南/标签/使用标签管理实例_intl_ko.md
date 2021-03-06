## 작업 시나리오

**태그**는 Tencent Cloud가 클라우드 상의 리소스 식별을 위해 제공하는 표기로, 키-값 쌍(Key-Value)을 말합니다. 태그를 사용하여 다양한 각도(예: 비즈니스, 용도, 담당자 등)에서 CVM 리소스를 분류 및 관리할 수 있습니다.
Tencent Cloud는 사용자가 설정한 태그를 사용하지 않습니다. 태그는 사용자의 서버 리소스 관리에만 사용됩니다.

## 사용 제한
태그를 사용할 때 다음과 같은 제한 조건에 유의해야 합니다.
- 수량 제한: 각 클라우드 리소스마다 허용되는 최대 태그 수량은 50입니다.
- 태그 키 제한: 
 - ‘qcloud’, ‘tencent’, ‘project’로 시작하는 시스템 예약 태그 키는 생성을 금지합니다.
 - ‘숫자’, ‘알파벳’, ‘+=.@-’만 사용 가능하며, 태그 키의 최대 길이는 255자로 제한합니다.
- 태그 값 제한: ‘공백 문자 혹은 숫자’, ‘알파벳’, ‘+=.@-’만 사용 가능하며, 태그 값의 최대 길이는 127자로 제한합니다.

## 작업 방법 및 사례

### 사례 설명

사례: 모 회사에서 CVM 인스턴스 6대를 구매하였습니다. 이 6대의 인스턴스를 사용하는 부서, 비즈니스 범위 및 담당자 정보는 다음과 같습니다.

| 인스턴스 instance-id | 사용 부서 | 비즈니스 범위 | 담당자 |
|---------|---------|---------|--------|
| ins-abcdef1 | 전자상거래 | 마케팅 이벤트 | 장 씨 |
| ins-abcdef2 | 전자상거래 | 마케팅 이벤트 | 왕 씨 |
| ins-abcdef3 | 게임 | 게임 A | 이 씨 |
| ins-abcdef4 | 게임 | 게임 B | 왕 씨 |
| ins-abcdef5 | 문화 엔터테인먼트 | 후반 작업 | 왕 씨 |
| ins-abcdef6 | 문화 엔터테인먼트 | 후반 작업 | 장 씨 |

ins-abcdef1을 예로 들어 해당 인스턴스에 다음과 같은 세 그룹의 태그를 추가할 수 있습니다.
<table id="table02">
	<tr><th>태그 키</th><th>태그 값</th></tr>
	<tr><td>dept</td><td>ecommerce</td></tr>
	<tr><td>business</td><td>mkt</td></tr>
	<tr><td>owner</td><td>zhangsan</td></tr>
</table>

이와 마찬가지로 기타 인스턴스 또한 사용 부서, 비즈니스 범위 및 담당자에 따라 그에 해당하는 태그를 설정할 수 있습니다.

### CVM 콘솔에서 태그 설정
상기 시나리오를 예로 들어, 사용자는 태그 키와 태그 값의 기획을 완료한 후 CVM 콘솔에 로그인하여 태그를 설정할 수 있습니다.

1. [CVM 콘솔](https://console.cloud.tencent.com/cvm)에 로그인합니다.
2. 인스턴스 관리 페이지에서 태그를 편집할 인스턴스를 선택하고 [More]>[Instance Settings]>[Edit Tags]을 클릭합니다. 아래 그림 참조
![](https://main.qcloudimg.com/raw/956e2cf2c732fde19f54eef9fabb0cf4.png)
2. 팝업된 "클라우드 리소스 1개를 선택하였습니다" 창에서 태그를 설정합니다. 아래 그림 참조
예를 들어, ins-abcdef1 의 인스턴스에 [세 그룹 태그](#table02)를 추가합니다.
![](https://main.qcloudimg.com/raw/42b543c329252587a758034d1a46c95a.png)
3. [OK]을 클릭하면 시스템에 수정 성공 알림이 나타납니다.


### 태그를 통해 인스턴스 필터링

사용자는 어떠한 태그의 인스턴스를 필터링 하고자 할 경우, 다음 작업을 통해 필터링할 수 있습니다.

1. 검색창에서 [Tag]를 선택합니다.
2. [Tag:] 뒤에 태그 키와 태그 값을 입력하고 <img src="https://main.qcloudimg.com/raw/3cca38f08eaa87087cdd1b81eaf08a0a.png" style="margin: 0;">을 클릭하여 검색합니다. 아래 그림 참조
예를 들어, 담당자가 장 씨인 리소스를 필터링하려면 `태그:owner:zhangsan`을 입력하면 됩니다.
![](https://main.qcloudimg.com/raw/6d65de3197540c1ccbe56b716ed44eab.jpg)

