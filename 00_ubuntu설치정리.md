#VMware 설치하기
---------------------------------------------------------------
###**VMware란?**
가상머신의 한 종류. 가상머신은 PC에 설치되어 있는 운영체제에 가상의 PC을 생성한 후 여기에 다른 운영체제나 응용 프로그램을 설치할 수 있도록 해주는 소프트웨어. 우리가 사용할 가상머신은 VM Workstation Player.
>**1.<http://www.vmware.com/kr> 로 이동**
다운로드 >>무료 제품 다운로드 >> Workstation Player >> Download

* 아래 캡쳐 화면에서 위의 것을 다운로드 합니다.

![vm1](https://i.imgur.com/eVpCMia.png)

>**2.다운로드 후 설치 시작**
라이선스 동의 화면에서 I accept the terms in the License Agreement 에 체크하여 동의하고 Next를 누르며 진행

![vm2-1](https://i.imgur.com/a7sTAX3.png)
![vm2-2](https://i.imgur.com/iFiN9w7.png)
![vm2-3](https://i.imgur.com/YGpxjV9.png)
![vm2-4](https://i.imgur.com/VU6Zh6X.png)
![vm2-5](https://i.imgur.com/RPRPEIU.png)
![vm2-6](https://i.imgur.com/5EeqtxJ.png)
![vm2-7](https://i.imgur.com/xtAOKy6.png)
![vm2-8](https://i.imgur.com/kRN2YSy.png)

>**3. 설치 완료 후 실행**

![vm3-1](https://i.imgur.com/hOUugyU.png)
![vm3-2](https://i.imgur.com/HxMYXUB.png)

* VMware를 실행하면 다음과 같은 화면을 만날 수 있습니다.

![vm3-3](https://i.imgur.com/ncXXEpr.png)


#Ubuntu 설치하기
------------------------------------------------------------
###**Ubuntu란?**
PC나 데스크탑에서 쉽게 사용할 수 있게 만들어진 리눅스 OS의 배포판. 데비안 GNU/리눅스에 기반하며 유니티라는 독자적인 데스크톱 환경을 사용. 전세계 누구나 어렵지 않게 오픈소스 소프트웨어를 사용할 수 있게 헌신하자는 우분투의 기본 철학에 따라, 우분투는 누구나 손쉽게 설치하고 사용할 수 있음.

>**1. 우분투 설치 전 가상으로 하드디스크 만들기**

* VMware Workstation Player를 실행하고 Create a New Virtual Machine을 누릅니다.

![u1-1](https://i.imgur.com/tKMAodC.png)

* 아래 화면에서 I will install the operating system later를 선택합니다. 이는 하드디스크만 생성하고 나중에 운영체제를 설치하는 과정입니다. 우분투를 설치할 것이므로 Linux를 선택합니다.

![u1-2](https://i.imgur.com/kUl1Yfs.png)
![u1-3](https://i.imgur.com/oDpuzEQ.png)


* 설치경로를 설정합니다. 디스크 파일의 용량을 지정할 때는 기본값 20GB로 합니다. 가상으로 지정하기 때문에 실제로 이 공간을 차지하는 건 아닙니다.

![u1-4](https://i.imgur.com/B2Qunlp.png)
![u1-5](https://i.imgur.com/kqcDbkh.png)

* 정보 확인 후 Finish를 누릅니다.

![u1-6](https://i.imgur.com/BgkJ61K.png)

* 완료하면 다음과 같은 화면을 만날 수 있습니다.

![u1-7](https://i.imgur.com/HX1Unqh.png)

>**2. 우분투를 설치하기 위해 ISO 파일을 다운**
**<http://www.ubuntu.com/>으로 이동**   
Download >> Desktop

* Ubuntu LTS를 다운 받습니다. LTS는 Long Term Support의 약자로 5년 동안 보안 업데이트를 제공합니다.

![u2-1](https://i.imgur.com/yDyDmx1.png)
![u2-2](https://i.imgur.com/xqfTFi0.png)
![u2-3](https://i.imgur.com/pcQtYtP.png)

>**3. 가상머신이 ISO파일을 인식할 수 있게 지정**

* Edit virtual machine settings를 누릅니다.

![u3-1](https://i.imgur.com/13SSBDf.png)

* 설정창이 뜨면 메모리 크기를 4GB로 조정합니다.

![u3-2](https://i.imgur.com/debDj8o.png)

* CD/DVD 항목을 선택하고 Connection에서 Use ISO image file을 선택합니다. Browse 버튼을 클릭해 다운로드 받은 우분투의 ISO파일을 선택합니다.

![u3-3](https://i.imgur.com/7pTitak.png)

>**4. 우분투 설치**

* Play virtual machine을 누르면 정상적으로 Ubuntu 설치가 시작됩니다.

![u4-1](https://i.imgur.com/c5SMV6w.png)
![u4-2](https://i.imgur.com/6URzcLa.png)

* 한국어를 선택하고 Ubuntu 설치를 선택합니다.

![u4-3](https://i.imgur.com/lpYvh5j.png)

* 위의 항목만 체크를 하고 계속을 누릅니다.

![u4-4](https://i.imgur.com/ky5Zx0f.png)

* ‘디스크를 지우고 Ubuntu 설치’를 선택하고 ‘지금 설치’를 누릅니다.
다음과 같이 위치, 키보드, 계정 설정을 합니다.

![u4-5](https://i.imgur.com/lylImdm.png)
![u4-6](https://i.imgur.com/6NJVVBi.png)
![u4-7](https://i.imgur.com/Y3ELzJo.png)
![u4-8](https://i.imgur.com/fdQzttH.png)

* 모든 설정을 완료하면 설치가 시작됩니다. 설치 완료 후 재시작을 해줍니다.

![u4-9](https://i.imgur.com/T3sveIf.png)
![u4-10](https://i.imgur.com/uvCyZB6.png)

* 재시작 후 다음과 같은 화면이 나타납니다. 바로 나타나지 않으면 Power Off 버튼을 눌러 VMware를 종료하고 다시 실행합니다.

![u4-11](https://i.imgur.com/JbDzdC0.png)
![u4-12](https://i.imgur.com/2PqGTwb.png)

* 비밀번호를 입력하고 로그인 하면 다음과 같은 화면이 나타납니다.

![u4-13](https://i.imgur.com/E9N4So0.png)

* 이상으로 정상적인 Ubuntu 설치가 완료되었습니다.
