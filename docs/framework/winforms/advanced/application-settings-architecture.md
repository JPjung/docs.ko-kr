---
title: 애플리케이션 설정 아키텍처
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 717abc8f54669a5ca814a61827a0865215204e1b
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487350"
---
# <a name="application-settings-architecture"></a>애플리케이션 설정 아키텍처
이 항목에서는 애플리케이션 설정 아키텍처가 작동하는 방식과 그룹화된 설정 및 설정 키와 같은 고급 아키텍처 기능에 대해 설명합니다.  
  
 애플리케이션 설정 아키텍처에서는 애플리케이션 범위 또는 사용자 범위로 강력한 형식의 설정을 정의하고 애플리케이션 세션 간에 설정을 유지할 수 있습니다. 또한 이 아키텍처는 로컬 파일 시스템에 설정을 저장하고 해당 시스템에서 설정을 로드하기 위한 기본 지속성 엔진을 제공하며, 사용자 지정 지속성 엔진을 제공하기 위한 인터페이스도 정의합니다.  
  
 애플리케이션에서 사용자 지정 구성 요소를 호스팅할 때 구성 요소 자체의 설정을 유지할 수 있도록 하는 인터페이스가 제공됩니다. 설정 키를 사용하면 구성 요소에서 구성 요소의 여러 인스턴스에 대한 설정을 개별적으로 유지할 수 있습니다.  
  
## <a name="defining-settings"></a>설정 정의  
 응용 프로그램 설정 아키텍처는 Windows Forms 및 ASP.NET에서 사용 되 고 두 환경 간에 공유 되는 기본 클래스의 번호를 포함 합니다. 가장 중요 한 <xref:System.Configuration.SettingsBase>는 컬렉션을 통해 설정에 대 한 액세스를 제공 하며 설정 로드 및 저장에 대 한 하위 수준 메서드를 제공 합니다. 파생 된 고유한 클래스를 구현 하는 각 환경 <xref:System.Configuration.SettingsBase> 해당 환경에 대 한 추가 설정 기능을 제공 합니다. Windows Forms 기반 응용 프로그램을 모든 응용 프로그램 설정에서 파생 된 클래스에 정의 되어야 합니다는 <xref:System.Configuration.ApplicationSettingsBase> 기본 클래스에는 다음과 같은 기능을 추가 하는 클래스:  
  
- 상위 수준 로드 및 저장 작업  
  
- 사용자 범위 설정 지원  
  
- 사용자 설정을 미리 정의된 기본값으로 되돌리기  
  
- 이전 애플리케이션 버전에서 설정 업그레이드  
  
- 변경하거나 저장하기 전에 설정에 대한 유효성 검사  
  
 내에서 정의 된 특성의 수를 사용 하 여 설정을 설명할 수 있습니다 합니다 <xref:System.Configuration> 네임 스페이스에 설명 된 이러한 [응용 프로그램 설정 특성](application-settings-attributes.md)합니다. 설정을 정의 사용 하 여 적용 해야 합니다 <xref:System.Configuration.ApplicationScopedSettingAttribute> 또는 <xref:System.Configuration.UserScopedSettingAttribute>, 설정을 전체 응용 프로그램 또는 현재 사용자에만 적용 되는지 여부를 설명 합니다.  
  
 다음 코드 예제에서는 단일 설정인 `BackgroundColor`를 사용하여 사용자 지정 설정 클래스를 정의합니다.  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>설정 지속성  
 합니다 <xref:System.Configuration.ApplicationSettingsBase> ; 클래스에서 파생 되는 설정 공급자에 게 이러한 작업은 클래스 자체를 유지 하거나 하지 설정을 로드할 <xref:System.Configuration.SettingsProvider>합니다. 파생 클래스가 <xref:System.Configuration.ApplicationSettingsBase> 를 통해 설정 공급자를 지정 하지 않습니다를 <xref:System.Configuration.SettingsProviderAttribute>, 다음 기본 공급자를 <xref:System.Configuration.LocalFileSettingsProvider>, 사용 됩니다.  
  
 .NET Framework를 사용 하 여 원래 릴리스된 구성 시스템 지원 또는 로컬 컴퓨터의 machine.config 파일을 통해 정적 응용 프로그램 구성 데이터를 제공 하는 `app.`exe.config 파일을 사용 하 여 배포 응용 프로그램입니다. <xref:System.Configuration.LocalFileSettingsProvider> 클래스는 다음과 같은 방법으로이 기본 지원을 확장 합니다.  
  
- 애플리케이션 범위 설정은 machine.config 또는 `app.`exe.config 파일에 저장될 수 있습니다. Machine.config는 항상 읽기 전용이지만, `app`.exe.config는 보안 고려 사항에 따라 대부분의 애플리케이션에서 읽기 전용으로 제한됩니다.  
  
- 사용자 범위 설정은 `app`.exe.config 파일에 저장될 수 있으며, 이 경우 정적 기본값으로 처리됩니다.  
  
- 기본값이 아닌 사용자 범위 설정은 새 파일인 *user*.config에 저장되며, 여기서 *user*는 현재 애플리케이션을 실행 중인 사람의 사용자 이름입니다. 사용 하 여 사용자 범위 설정에 대 한 기본값을 지정할 수 있습니다 <xref:System.Configuration.DefaultSettingValueAttribute>합니다. 사용자 범위 설정이 애플리케이션 실행 중에 자주 변경되기 때문에 `user`.config는 항상 읽기/쓰기입니다.  
  
 세 가지 구성 파일은 모두 설정을 XML 형식으로 저장합니다. 애플리케이션 범위 설정의 최상위 XML 요소는 `<appSettings>`이며, 사용자 범위 설정에는 `<userSettings>`가 사용됩니다. 애플리케이션 범위 설정과 사용자 범위 설정의 기본값을 모두 포함하는 `app`.exe.config 파일은 다음과 같습니다.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
 구성 파일의 애플리케이션 설정 섹션에 있는 요소의 정의는 [애플리케이션 설정 스키마](../../configure-apps/file-schema/application-settings-schema.md)를 참조하세요.  
  
### <a name="settings-bindings"></a>설정 바인딩  
 애플리케이션 설정은 Windows Forms 데이터 바인딩 아키텍처를 사용하여 설정 개체와 구성 요소 간의 양방향 통신으로 설정 업데이트를 제공합니다. Visual Studio에서 애플리케이션 설정을 만들어 구성 요소 속성에 할당하면 이러한 바인딩이 자동으로 생성됩니다.  
  
 응용 프로그램 설정을 지 원하는 구성 요소에만 바인딩할 수 있습니다는 <xref:System.Windows.Forms.IBindableComponent> 인터페이스입니다. 구성 요소 특정 바인딩 속성 변경 이벤트를 구현 하거나 응용 프로그램 설정 속성을 통해 변경 되었음을 알리는 해야 또한는 <xref:System.ComponentModel.INotifyPropertyChanged> 인터페이스입니다. 구성 요소를 구현 하지 않는 경우 <xref:System.Windows.Forms.IBindableComponent> 및 Visual Studio를 통해 바인딩, 바인딩된 속성을 처음으로 설정 되지만 업데이트 되지 것입니다. 구성 요소를 구현 하는 경우 <xref:System.Windows.Forms.IBindableComponent> 않습니다 하지 속성 변경 알림을 지원 하지만 속성이 변경 될 때 바인딩은 설정 파일에서 업데이트 되지 것입니다.  
  
 일부 Windows Forms 구성 요소와 같은 <xref:System.Windows.Forms.ToolStripItem>, 설정 바인딩을 지원 하지 않습니다.  
  
### <a name="settings-serialization"></a>설정 직렬화(Serialization)  
 때 <xref:System.Configuration.LocalFileSettingsProvider> 설정을 디스크에 저장 해야 다음 작업을 수행 합니다.  
  
1. 리플렉션을 사용 하 여 모두에 정의 된 속성을 검사 하 여 <xref:System.Configuration.ApplicationSettingsBase> 파생 클래스를 사용 하 여 적용 되는 찾기 <xref:System.Configuration.ApplicationScopedSettingAttribute> 또는 <xref:System.Configuration.UserScopedSettingAttribute>합니다.  
  
2. 속성을 디스크에 직렬화합니다(serialize). 먼저 호출 하려고 합니다 <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> 또는 <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> 에서 연관 된 형식을 <xref:System.ComponentModel.TypeConverter>합니다. 호출하지 못하면 XML serialization을 대신 사용합니다.  
  
3. 설정의 특성에 따라 어떤 파일에 어떤 설정을 사용할지 결정합니다.  
  
 사용자 고유의 설정 클래스를 구현 하는 경우 사용할 수 있습니다 합니다 <xref:System.Configuration.SettingsSerializeAsAttribute> 사용 하 여 이진 또는 사용자 지정 serialization에 대 한 설정을 표시 하는 <xref:System.Configuration.SettingsSerializeAs> 열거형입니다. 코드에서 사용자 고유의 설정 클래스를 만드는 방법에 대 한 자세한 내용은 참조 하세요. [방법: 응용 프로그램 설정 만들기](how-to-create-application-settings.md)합니다.  
  
### <a name="settings-file-locations"></a>설정 파일 위치  
 `app`.exe.config 및 *user*.config 파일의 위치는 응용 프로그램을 설치하는 방법에 따라 다릅니다. 로컬 컴퓨터에 복사 하는 Windows Forms 기반 응용 프로그램에 대 한 `app`합니다. 응용 프로그램의 주 실행 파일의 기본 디렉터리와 같은 디렉터리의 exe.config 상주할 및 *사용자*.config에 상주할 합니다 지정 된 위치는 <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> 속성입니다. ClickOnce를 사용 하 여 설치 된 응용 프로그램을 위해 이러한 파일은 모두 상주할 %InstallRoot%\Documents 아래 ClickOnce 데이터 디렉터리 및 설정을\\*username*\Local Settings입니다.  
  
 사용자가 로밍 프로필을 사용하도록 설정한 경우 한 도메인 내에서 다른 컴퓨터를 사용할 때 다른 Windows 및 애플리케이션 설정을 정의할 수 있으므로 이러한 파일의 저장 위치는 약간 다릅니다. ClickOnce 응용 프로그램 및 비 ClickOnce 응용 프로그램을 모두 해야 경우 해당 `app`..exe.config로 지정 하 고 *사용자*.config 파일이 %InstallRoot%\Documents and Settings 아래에 저장\\  *사용자 이름*\Application Data.  
  
 애플리케이션 설정 기능이 새로운 배포 기술을 통해 작동하는 방법에 대한 자세한 내용은 [ClickOnce 및 애플리케이션 설정](/visualstudio/deployment/clickonce-and-application-settings)을 참조하세요. ClickOnce 데이터 디렉터리에 대 한 자세한 내용은 참조 하세요. [로컬 및 ClickOnce 응용 프로그램의 원격 데이터 액세스](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications)합니다.  
  
## <a name="application-settings-and-security"></a>애플리케이션 설정 및 보안  
 애플리케이션 설정은 인터넷이나 인트라넷에서 호스팅되는 Windows Forms 애플리케이션의 기본적인 제한된 환경인 부분 신뢰 환경에서 작동하도록 설계되었습니다. 기본 설정 공급자를 포함한 애플리케이션 설정을 사용하는 데에는 부분 신뢰 권한만 필요합니다.  
  
 ClickOnce 응용 프로그램에서는 응용 프로그램 설정을 사용 하는 경우는 `user`.config 파일은 ClickOnce 데이터 디렉터리에 저장 합니다. 응용 프로그램의 크기 `user`.config 파일이 ClickOnce를 통해 설정 된 데이터 디렉터리 할당량을 초과할 수 없습니다. 자세한 내용은 [ClickOnce 및 애플리케이션 설정](/visualstudio/deployment/clickonce-and-application-settings)을 참조하세요.  
  
## <a name="custom-settings-providers"></a>사용자 지정 설정 공급자  
 응용 프로그램 설정 아키텍처에 있어서 응용 프로그램 설정 간의 느슨한 결합을에서 파생 된 래퍼 클래스 <xref:System.Configuration.ApplicationSettingsBase>와 연결 된 설정 공급자 또는 공급자의 경우 파생 된 <xref:System.Configuration.SettingsProvider>합니다. 이 연결을 에서만 정의 <xref:System.Configuration.SettingsProviderAttribute> 래퍼 클래스 또는 해당 개별 속성에 적용 합니다. 설정 공급자가 없습니다 명시적으로 지정 하면 기본 공급자 인 <xref:System.Configuration.LocalFileSettingsProvider>에 사용 됩니다. 따라서 이 아키텍처는 사용자 지정 설정 공급자를 만들고 사용할 수 있도록 지원합니다.  
  
 예를 들어 Microsoft SQL Server 데이터베이스에 모든 설정 데이터를 저장하는 공급자인 `SqlSettingsProvider`를 개발하여 사용한다고 가정합니다. 프로그램 <xref:System.Configuration.SettingsProvider>-파생된 클래스에서이 정보를 수신할 해당 `Initialize` 메서드에 형식 매개 변수로 <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>합니다. 다음을 구현 합니다 <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> 데이터 저장소에서 설정을 검색 하는 방법 및 <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> 저장. 공급자에 사용할 수는 <xref:System.Configuration.SettingsPropertyCollection> 에 제공 된 <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> 속성의 이름, 유형 및 범위를 확인 하려면 다른 설정 특성 및 해당 속성에 대해 정의 합니다.  
  
 공급자는 구현이 분명하지 않은 속성 하나와 메서드 하나를 구현해야 합니다. 합니다 <xref:System.Configuration.SettingsProvider.ApplicationName%2A> 속성의 추상 속성은 <xref:System.Configuration.SettingsProvider>; 다음을 반환 하도록 프로그래밍 해야 합니다.  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 또한 파생 클래스는 인수를 사용하지 않고 값을 반환하지 않는 `Initialize` 메서드도 구현해야 합니다. 이 메서드는 정의 되지 않은 <xref:System.Configuration.SettingsProvider>합니다.  
  
 마지막으로 구현 <xref:System.Configuration.IApplicationSettingsProvider> 설정 새로 고침에 대 한 지원을 제공 하 여 공급자에서 설정을 기본값으로 되돌리기 및 다른 설정을 응용 프로그램 버전에서 업그레이드 합니다.  
  
 공급자를 구현하고 컴파일했으면 설정 클래스에서 기본값 대신 이 공급자를 사용하도록 지시해야 합니다. 통해이 작업을 수행 합니다 <xref:System.Configuration.SettingsProviderAttribute>합니다. 전체 설정 클래스에 적용 하는 경우 해당 공급자가; 클래스를 정의 하는 각 설정에 대 한 사용 개별 설정에 적용 하는 경우 응용 프로그램 설정 아키텍처에만 해당 설정에 대 한 해당 공급자를 사용 하 고이 사용 하는 <xref:System.Configuration.LocalFileSettingsProvider> 나머지 부분에 대 한 합니다. 다음 코드 예제에서는 사용자 지정 공급자를 사용하도록 설정 클래스에 지시하는 방법을 보여 줍니다.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 한 공급자를 여러 스레드에서 동시에 호출할 수 있지만, 공급자가 항상 동일한 저장소 위치에 쓰므로 애플리케이션 아키텍처는 공급자 클래스의 단일 인스턴스만 인스턴스화합니다.  
  
> [!IMPORTANT]
>  공급자가 스레드로부터 안전하며 구성 파일에 쓸 수 있는 스레드를 한 번에 하나씩 허용하는지 확인해야 합니다.  
  
 공급자는 특성에 정의 된 설정 중 일부를 지원 하지 않아도 <xref:System.Configuration?displayProperty=nameWithType> 네임 스페이스 최소 지원 해야 하지만 <xref:System.Configuration.ApplicationScopedSettingAttribute> 및 <xref:System.Configuration.UserScopedSettingAttribute>에 지원 해야 <xref:System.Configuration.DefaultSettingValueAttribute>합니다. 지원하지 않는 특성에 대해서는 공급자가 알림 없이 실패해야 하며 예외를 throw하면 안됩니다. 하지만 설정 클래스에서 특성의 조합이 잘못를 사용 하는 경우-적용 하는 등 <xref:System.Configuration.ApplicationScopedSettingAttribute> 고 <xref:System.Configuration.UserScopedSettingAttribute> 같은 설정으로-공급자에서 예외를 throw 하 고 작업을 중단 해야 합니다.  
  
## <a name="see-also"></a>참고자료

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [응용 프로그램 설정 개요](application-settings-overview.md)
- [사용자 지정 컨트롤에 대한 응용 프로그램 설정](application-settings-for-custom-controls.md)
- [ClickOnce 및 응용 프로그램 설정](/visualstudio/deployment/clickonce-and-application-settings)
- [응용 프로그램 설정 스키마](../../configure-apps/file-schema/application-settings-schema.md)
