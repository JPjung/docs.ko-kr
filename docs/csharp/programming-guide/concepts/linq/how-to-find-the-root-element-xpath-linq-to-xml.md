---
title: '방법: 루트 요소 찾기(XPath 및 LINQ to XML)(C#)'
ms.date: 07/20/2015
ms.assetid: 4fd824e0-4d39-429b-b092-f6a5c046ee6c
ms.openlocfilehash: 59696e6f3487bbb09135ba413a173c32dffa0c9b
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485418"
---
# <a name="how-to-find-the-root-element-xpath-linq-to-xml-c"></a>방법: 루트 요소 찾기(XPath 및 LINQ to XML)(C#)
이 항목에서는 XPath와 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]을 사용하여 루트 요소를 가져오는 방법을 보여 줍니다.  
  
 XPath 식은 다음과 같습니다.  
  
 `/PurchaseOrders`  
  
## <a name="example"></a>예제  
 이 예제에서는 루트 요소를 찾습니다.  
  
 이 예제에서는 XML 문서로을 사용합니다. [샘플 XML 파일: 여러 구매 주문(LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-multiple-purchase-orders-linq-to-xml.md).  
  
```csharp  
XDocument po = XDocument.Load("PurchaseOrders.xml");  
  
// LINQ to XML query  
XElement el1 = po.Root;  
  
// XPath expression  
XElement el2 = po.XPathSelectElement("/PurchaseOrders");  
  
if (el1 == el2)  
    Console.WriteLine("Results are identical");  
else  
    Console.WriteLine("Results differ");  
Console.WriteLine(el1.Name);  
```  
  
 이 예제는 다음과 같은 출력을 생성합니다.  
  
```  
Results are identical  
PurchaseOrders  
```  
