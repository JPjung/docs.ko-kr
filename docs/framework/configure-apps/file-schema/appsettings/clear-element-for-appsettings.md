---
title: <appSettings>에 대한 <clear> 요소
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d4d96143dbd1db440de2247a7dc2f0c66f20403
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301290"
---
# <a name="clear-element-for-appsettings"></a>\<지우기 > 요소에 대 한 \<appSettings >

사용자 지정 응용 프로그램 설정을 지웁니다.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>구문

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>특성

없음

## <a name="parent-element"></a>부모 요소

|     | 설명 |
| --- | ----------- |
| [ **\<appSettings>** ](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | 파일 경로, XML 웹 서비스 Url 또는 기타 사용자 지정 응용 프로그램 구성 정보와 같은 사용자 지정 응용 프로그램 설정을 포함합니다. |

## <a name="child-elements"></a>자식 요소

없음

## <a name="example"></a>예제

다음 예제에서는 사용자 지정 구성 설정의 선택을 취소 하는 방법을 보여 줍니다.

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>참고자료

- [.NET Framework의 구성 파일 스키마](~/docs/framework/configure-apps/file-schema/index.md)
