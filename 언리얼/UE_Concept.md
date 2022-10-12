# 문법 c

## 기본 개념
게임 모드  
- 처음 배정되는 캐릭터 수, 클리어 정보 활성할때  
- 레벨당 1개 


------------------

## BluePrint 

ABS: 절대값  
Pure함수: 컴파일러가 자동으로 실행해줌으로서 연결된 노드마다 한번씩 호출  



상대창을 불리언으로 관리하지말고 Stat만들어서 관리
HUD는 아주 간단한 UI 사용할떄 고려  
애니메이션을 한곳에 몰빵해서 관리

Sequence  
For문  실패하면 빠져나감

Selector  
switch case문 

---------
## C++

UPROPERTY() 멤버 변수앞 선언해야함으로써 언리얼 인식을 위해 사용  
Visible, Edit +  
DefaultsOnly(블루프린트에서만), InstanceOnly(월드상에 오브젝트에서만), Anywhere  
EX) EditAnywhere  
  

Ue_LOG('로그 카테고리','상세수준,'로그내용')  
>로그 카테고리   
LOG: 파일출력 O/ 콘솔X  
Warning: 콘솔및로그O 노란색표시  
Error: 콘솔및로그O 빨간색으로표시  
Display: 파일콜솔출력O  
(TEXT""), 뒤에 자료형 같은경우 %d,%c.. 으로 가능

is valid: 널 체크 

FRotator: 회전 pitch, roll yaw
  

DelGate   
어떤행동이 끝날떄 실행시키는 함수
BroadCast() 
구독한 애들한테 알림  

디버깅  
>debugGame: 최적화 덜됬지만 심볼이 젤 많아 개발단계에서 가장 많이 사용  
development 최적화 됬지만 심보 날라감




블루프린트 갖고올때 맨뒤 _C붙이기

--------
CharacterMovementComponent : 캐릭터 이동에 관여  
ConstructorHelpers  생성자코드에서 에셋 관련된 정보를 불러올때 사용 (생성자에서만 사용)
CharacterMeshComponent -> 뼈대 애니메이션 , 충돌  

CapsuleComponent 충돌 범위  
SetUpAttachment 붙이는거  
virtual void NativeUpdateAnimation(float DeltaSeconds) override; 한틱씩 애니메이션   

AIControllerClass ->폰에  기본적으로 등록할 AI   
GetActorLocation 현재 위치  
UBoxComponent << 충돌  
OwerComp.GetAIOwner << 정보  

-------------------
컨테이너 보관

기존에 c++ 있던 vector map unorder_map 사용 X  
vector - TArray //Empty는 clear()와 같다  
map unordered_map - TMap  
string - TString   


----------------------
네비게이션  
if(NavSystem->GetRandomPointInNavigableRadius(FVector::ZeroVector,500.f,RandomLocation))
{
	UAIBlueprintHelperLibrary::SimpleMoveToLocation(this,RandomLocation);
}