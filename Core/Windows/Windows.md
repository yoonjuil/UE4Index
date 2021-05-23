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
	* 대상의 값이 0이면 대상의 값을 가져오고 0으로 설정한다.
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
	
* Is64bitOperatingSystem

	* 64bit OS 인지 확인한다.

* IsValidAbsolutePathFormat

	* 절대 경로 형식이 맞는지 검사한다.

* NumberOfCores

	* 코어수를 반환한다.

* NumberOfCoresIncludingHyperthreads

	* 하이퍼쓰레드를 포함한 코어의 수를 반환한다.

* NumberOfWorkerThreadsToSpawn

	* 데디케이트서버인 경우에는 최대 4개로 제한된 작업 쓰레드 수를 반환한다.
	* 데이케이트 서버가 아닌 경우에는 최대 26개의 작업 쓰레드 수를 반환한다.

* OsExecute

	* Windows Shell 을 이용하여 Command 를 실행한다.

* SetStoreValue

	* Current User / Software 레지스트리에 값을 저장한다.

* GetStoreValue

	* Current User / Software 레지스트리에 있는 값을 읽어온다.

* DeleteStoredValue

	* Current User / Software 레지스트리에 있는 키를 삭제한다.

* GetDefaultLanguage

	* 언어 이름 형식으로 가장 첫번째 언어를 반환한다.

	* ko-KR

	* https://docs.microsoft.com/en-us/windows/win32/intl/language-names

	* 윈도우8 미만에서는 GetDefaultLocale 을 사용한다.

	* ```c++
		GetUserPreferredUILanguages
		```

* GetDefaultLocale

	* 기본 사용자 로케일 이름을 반환한다.

	* <language>-<REGION>

	* en-US

	* https://docs.microsoft.com/en-us/windows/win32/intl/locale-names

	* ```c++
		GetUserDefaultLocaleName
		```

* GetCPUVendor

	* CPU Vendor 이름을 반환한다.

* GetCPUBrand

	* CPU Brand 이름을 반환한다.

* GetPrimaryGPUBrand

	* 첫번째 GPU Brand이름을 반환한다.

* GetOSVersion

	* OS Version을 반환한다.

* GetDiskTotalAndFreeSpace

	* 경로의 디스크의 전체 용량과 빈 용량을 반환한다.

* QueryRegKey

	* 레지스트리에서 특정 경로의 있는 값을 가져온다.
	* 값의 정확한 길이를 알 수 없을 경우에 사용한다.

* IsRunningOnBattery

	* 배터리로 실행중인지 알아낸다.
	* GetSystemPowerStatus 를 사용한다.

* GetOperatingSystemId

	* OS 가 설치될때 생성된 고유한 시스템 id 를 가져온다.

## FWindwosCriticalSection

* FWindowsCriticalSection
	* CriticalSection 을 생성한다.
* FWindowsSystemWideCriticalSection
	* Mutex를 이용한 시스템 전반적인 CriticalSection을 사용한다.
* FWindowsRWLock
	* RW Lock 을 사용한다.
	* https://docs.microsoft.com/en-us/windows/win32/sync/slim-reader-writer--srw--locks

## FWindowsPlatformProcess

* GetCurrentProcessId
	* 현재 프로세스 id 를 가져온다.
* GetCurrentCoreNumber
	* 현재 코어수를 반환한다.
* BaseDir
	* 실행파일이 있는 경로를 반환한다.
* UserDir
	* 내 문서안에 사용자 경로를 반환한다.
	* My Documents 경로이다.
	* "C:\Users\ibsof\Documents"
* UserTempDir
	* 임시 파일 경로를 반환한다.
	* "C:\Users\ibsof\AppData\Local\Temp"
* UserSettingsDir
	* 사용자 설정 경로를 반환한다.
	* AppData 경로이다.
	* "C:\Users\ibsof\AppData"
* ApplicationSettingsDir
	* ProgramData 경로를 반환한다.
	* "C:\ProgramData\Epic"
* ComputgerName
	* Computer 이름을 반환한다.
* UserName
	* UserName을 반환한다.
* SetCurrentWorkingDirectoryToBaseDir
	* 현재 작업 경로를 실행파일 경로로 설정한다.
* GetCurrentWorkingDirectory
	* 현재 작업 경로를 반환한다.
* ShaderWorkingDir
	* 쉐이더 작업 경로를 반환한다.
	* UserTempDir() / "UnrealShaderWorkingDir/" 이다.
* ExecutablePath
	* 실행파일이 있는 경로를 반환한다.
* ExecutableName
	* 실행파일명을 반환한다.
* GenerateApplicationPath
	* Engine/Binaries/ 하위에 Platform 에 따른 실행파일 경로를 생성한다.
	* 현재 시스템이 64비트일 경우 Development 용 실팽파일 A라면 Engine/Binaries/Win64/A-Win64-Development.exe 으로 생성된다.
* LaunchURL
	* schemeName이 http/https 인 경우 LaunchWebURL로 실행하고, 그렇지 않을 경우에는 LaunchDefaultHandlerForURL 을 실행한다.
	* LaunchDefaultHandlerForURL 은 ShellExecuteW 을 사용한다.
	* LaunchWebURL은 레지스트리에 등록된 기본 브라우저로 URL을 실행한다.
* GetApplicationMemoryUsage
	* 프로세스가 사용하고 있는 메모리 양을 반환한다.
* GetPerFrameProcessorUsage
	* 프로세스의 프레임을 반환한다.
* IsApplicationRunning
	* 프로세스가 실행중인지 확인한다.
* GetApplicationName
	* 프로세스의 애플리케이션 이름을 반환한다.



