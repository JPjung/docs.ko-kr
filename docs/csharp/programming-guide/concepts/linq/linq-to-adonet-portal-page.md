---
title: LINQ to ADO.NET(포털 페이지)
ms.date: 07/20/2015
ms.assetid: 6bd269b4-3509-4688-b672-836008704182
ms.openlocfilehash: 8c39582ee95619bfddc7b89380e0a86305eeac27
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539513"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET(포털 페이지)
LINQ to ADO.NET을 사용하면 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 프로그래밍 모델을 통해 ADO.NET의 열거 가능한 개체를 쿼리할 수 있습니다.  
  
> [!NOTE]
>  LINQ to ADO.NET 설명서는 .NET Framework SDK의 ADO.NET 섹션에 있습니다. [LINQ 및 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).  
  
 ADO.NET에는 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] 기술: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] 및 LINQ to Entities의 세 가지 독립적인 기술이 있습니다. LINQ to DataSet은 다양한 기능을 사용하여 <xref:System.Data.DataSet>에 대해 최적화된 쿼리를 제공하고, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]는 SQL Server 데이터베이스 스키마를 직접 쿼리하는 데 사용되며, LINQ to Entities는 엔터티 데이터 모델을 쿼리하는 데 사용됩니다.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet>는 ADO.NET에서 가장 널리 사용되는 구성 요소 중 하나이며, ADO.NET의 기반이 되는 연결되지 않은 프로그래밍 모델의 핵심 요소입니다. 그러나 이러한 탁월함에도 불구하고 <xref:System.Data.DataSet>의 쿼리 기능에는 한계가 있습니다.  
  
 LINQ to DataSet을 사용하면 다른 많은 데이터 원본에 사용되는 것과 같은 쿼리 기능을 사용하여 더 다양한 쿼리 기능을 <xref:System.Data.DataSet>에 빌드할 수 있습니다.  
  
 자세한 내용은 [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)을 참조하세요.  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]은 관계형 데이터를 개체로 관리하는 데 필요한 런타임 인프라를 제공합니다. [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 관계형 데이터베이스의 데이터 모델은 개발자의 프로그래밍 언어로 표현되는 개체 모델에 매핑됩니다. 애플리케이션을 실행하면 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 개체 모델의 언어 통합 쿼리를 SQL로 변환하여 실행을 위해 데이터베이스로 전송합니다. 데이터베이스가 결과를 반환하면 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에서 조작할 수 있는 개체로 다시 변환합니다.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]에는 데이터베이스의 저장 프로시저 및 사용자 정의 함수와 개체 모델의 상속을 지원합니다.  
  
 자세한 내용은 [LINQ to SQL](../../../../../docs/framework/data/adonet/sql/linq/index.md)을 참조하세요.  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 엔터티 데이터 모델을 통해 관계형 데이터는 .NET 환경에서 개체로 공개됩니다. 이를 통해 개체 계층은 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 지원을 위한 이상적인 대상이 되므로 개발자는 비즈니스 논리를 개발할 때 사용한 언어로 데이터베이스에 대한 쿼리를 작성할 수 있습니다. 이 기능은 LINQ to Entities로 알려져 있습니다. 자세한 내용은 [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md)를 참조하세요.  
  
## <a name="see-also"></a>참고 항목

- [LINQ 및 ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [LINQ(Language-Integrated Query)(C#)](../../../../csharp/programming-guide/concepts/linq/index.md)
