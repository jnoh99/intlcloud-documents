CFS 콘솔을 통해 파일 시스템 페이지에 파일 시스템 및 탑재 지점을 생성할 수 있습니다.
## 작업 절차

### 1. 파일 시스템 인터페이스에 진입
CFS 콘솔에 로그인하고 [파일 시스템] 왼쪽 탐색 모음을 클릭해 파일 시스템 인터페이스에 진입합니다.
![](https://main.qcloudimg.com/raw/236acda99de0c018174a3e7629bd18ae.png)

### 2. 파일 시스템 생성
[생성] 버튼을 클릭하면 파일 시스템 생성 팝업창이 표시됩니다. 팝업창에서 다음 정보를 선택하고 오류가 없음을 확인한 뒤 [확인]을 클릭하면 파일 시스템을 생성할 수 있습니다.
![](https://main.qcloudimg.com/raw/ef9e48b475c358e5a14d2b3499bb99e2.png)

- 지역: CFS가 지원하는 지역을 선택합니다.
- 가용 영역: CFS가 지원하는 가용 영역을 선택합니다.
- 파일 서비스 프로토콜: 파일 시스템 유형(NFS 또는 CIFS/SMB)을 선택합니다. NFS 프로토콜은 Linux 클라이언트에 더 적합하며 CIFS/SMB 프로토콜은 Windows 클라이언트에 더 적합합니다.
- 클라이언트 유형: CVM과 CPM은 각각 다른 네트워크에 소속되며 시스템은 접근 CVM 유형에 따라 해당 파일 시스템을 지정 네트워크에 분배합니다.
- 네트워크 유형: VPC 또는 기본 네트워크입니다. 자신의 CVM 인스턴스 소재 네트워크에 따라 파일 시스템을 생성 및 탑재하십시오.

	- VPC의 CVM에서 파일 시스템을 공유하려면 파일 시스템을 생성할 때 VPC를 선택해야 합니다. 파일 시스템이 VPC에 속할 경우, 특별한 네트워크 설정을 진행하지 않았다면 동일 VPC 내 CVM 인스턴스만 탑재할 수 있습니다.
	- 기본 네트워크의 CVM에서 파일 시스템을 공유하려면 파일 시스템을 생성할 때 기본 네트워크를 선택해야 합니다. 파일 시스템이 기본 네트워크에 속할 경우, 특별한 네트워크 설정을 진행하지 않았다면 동일 기본 네트워크 내 CVM 인스턴스만 탑재할 수 있습니다.
	- 여러 네트워크에서 파일 시스템을 공유하려면 [네트워크 간 파일 시스템 접근](https://cloud.tencent.com/document/product/582/9764) 문서를 참조하십시오.

- 권한 그룹: 모든 파일 시스템은 1개의 권한 그룹과 바인딩해야 합니다. 권한 그룹은 접근할 수 있는 화이트리스트 및 작업 권한을 규정하였습니다.

### 3. 탑재 지점 정보 획득
파일 시스템 및 탑재 지점 생성 완료 후, 이미 생성한 파일 시스템 이름을 클릭하여 파일 시스템 기본 정보 페이지에 진입한 뒤 [탑재 지점 정보]를 클릭하면 Linux의 탑재 명령 및 Windows의 탑재 명령을 확인 및 획득할 수 있습니다.
- 수량은 탑재 소스 수량, 즉 탑재할 수 있는 방식 수량입니다. 현재는 IP를 통한 탑재만 지원하기 때문에 이 값은 1입니다.

NFS 파일 시스템 탑재 지점 정보는 다음과 같습니다.
![](https://main.qcloudimg.com/raw/63f4f76c4f826f673aa009310fdf633c.png)

CIFS/SMB 파일 시스템 탑재 지점 정보는 다음과 같습니다.
![](https://main.qcloudimg.com/raw/33bfc3d0d7bae66c41fe0aa5cb0b0f16.png)

**주의: 프로토콜 호환 문제로 인하여 Docker 또는 Kubernetes 등 클라이언트를 사용하여 CFS를 탑재할 경우 NFS v3 프로토콜 사용을 권장합니다. NFS v4 프로토콜을 사용하면 일부 클라이언트는 정상 탑재할 수 없는 문제가 발생할 수 있습니다.**


