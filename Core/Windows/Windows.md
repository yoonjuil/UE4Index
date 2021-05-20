# Windows용 API

## FWindowsPlatformAtomics

Atomics OS Functions의 구현부이다.

Atomics 란? Interlocked API이다.

https://docs.microsoft.com/en-us/windows/win32/sync/interlocked-variable-access

Win32에서는 기본적으로 다음의 API를 가지고 있다.

* InterlockedIncrement (16bit / 32bit / 64bit)
	* 값을 1증가시킨다.
* InterlockedDecrement (16bit / 32bit / 64bit)
	* 값을 1감소시킨다.
* InterlockedAdd (8bit / 16bit / 32bit / 64bit)
	* 특정 값을 더한다.
* InterlockedExchange (8bit / 16bit / 32bit / 64bit)
	* 대상에 지정된 값으로 설정한다.
* InterlockedCompareExchange (8bit / 16bit / 32bit / 64bit)
	* 대상의 값이 비교값과 같으면 값을 설정한다.
* InterlockedAnd (8bit / 16bit / 32bit / 64bit)
	* 대상의 값을 AND 연산한다.
* InterlockedOr (8bit / 16bit / 32bit / 64bit)
	* 대상의 값을 Or 연산한다.
* InterlockedXor (8bit / 16bit / 32bit / 64bit)
	* 대상의 값을 Xor 연산한다.
* AtomicRead (8bit / 16bit / 32bit / 64bit)
	* 대상의 값을 읽어온다.
	* 대상의 값이 0이면 대상의 값을 가져오고 0으로 설정한다.
* AtomicRead_Relaxed (8bit / 16bit / 32bit / 64bit)
	* 대상의 값을 읽어온다.
* AtomicStore (8bit / 16bit / 32bit / 64bit)
	* 대상에 값을 설정한다.
* InterlockedExchangePtr
	* 대상에 값을 설정한다.

## FWindowsPlatformMisc

* GetMaxPathLength
	* 최대 경로 길이를 반환한다.
* GetEnvironmentVariable
	* 환경 변수의 값을 읽어온다.
	* https://docs.microsoft.com/en-us/windows/win32/api/processenv/nf-processenv-getenvironmentvariablew
	* https://docs.microsoft.com/en-us/windows/win32/procthread/environment-variables
* SetEnvironmentVariable
	* 환경 변수의 값을 지정한다.
* GetMacAddress
	* Mac Address를 읽어온다.
* IsDebuggerPresent (UE_BUILD_SHIPPING가 아닌 경우에만 사용 가능)
	* 현재 디버깅 중인지 확인한다.
* BeginNamedEventFrame / BeginNamedEvent / EndNamedEvent / CustomNamedStat
	* 프로파일러용
* IsRemoteSession
	* 원격에서 실행되었는지 확인한다.
* SetUTF8Output
	* stdout이 UTF8을 지원하도록 설정한다.
	* CommandLine 이 UTF8Output 로 지정되어 있어야 한다.
* LocalPrint
	* OutputDebugString으로 출력한다.
* RequestExit
	* 프로그램을 종료할 수 있도록 요청한다.
	* FCoreDelegates::ApplicationWillTerminateDelegate 이벤트를 발생시킨다.
* CreateGuid
	* GUID를 생성한다.
* MessageBoxExt
	* Win32 MessageBox 를 표시한다.
	* Ok / YesNo / OkCancel / YesNoCancel / CancelRetryContinue / YesNoYesAllNoAll / YesNoYesAllNoAllCancel / YesNoYesAll 형태가 있다.
* CommandLineCommands
	* CommandLine 에 firstinstall 이 입력되어 있고, 
	* 윈도우서버에서 실행되지 않고, 윈도우모드(풀스크린모드가 아닌것)로 실행되어 있다면 
	* 설치된 게임경로가 GameExplorer에 접근이 가능한 경우
	* WITH_FIREWALL_SUPPORT 가 아니라면
	* true를 반환한다.







