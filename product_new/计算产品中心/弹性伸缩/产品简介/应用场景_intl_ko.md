## 1. 사전에 용량 확장 및 축소를 할당합니다.
사전에 오토 스케일링 예약 정책을 설정하면 사용자는 수요에 따라 용량을 확장 및 축소할 수 있습니다. 해당 시점에서 시스템은 대기 없이 자동으로 CVM 용례를 추가하거나 감소합니다.

## 2. 저렴한 비용으로 서비스 요청 급증에 대응합니다.

사전에 서버를 준비하면 서비스 액세스 급증했을 때 CPU 증가로 인한 서버의 부하를 방지할 수 있고 부하가 해소되면 실제 부하에 따라 서버를 축소해야 합니다. 사용자는 사전에 오토 스케일링 모니터링 정책을 설정할 수 있으며, 시스템은 설정된 서비스 모니터링 지표에 따라 CVM 수평 확장이 필요한지 자동으로 판단합니다. 모니터링 지표이 임계 값에 도달하면 실시간 자동으로 CVM 용례를 증가하거나 감소하여 로드 밸런서 구성을 자동으로 완료합니다. 비용 절감은 물론 사용자가 수동으로 용량 확장할 필요가 없습니다.

## 3. 비정상 CVM을 자동으로 대체합니다.

비정상 클라우드 서버의 지속적인 실행이 서비스에 영향을 주지 않도록 사용자는 시스템의 CVM 실행 상태를 주시하고 수시로 처리해야 합니다. 시스템은 오토 스케일링을 사용하여 정기적으로 CVM의 상태를 확인하고, 비정상으로 실행 중인 CVM 용례를 검색하면 자동으로 1대의 용례를 수평 확장하여 비정상 용례를 대체합니다. 이 작업 레코드는 사용자가 볼 수 있도록 저장됩니다.
