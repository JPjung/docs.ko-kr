---
title: DataView에서 DataRowView 컬렉션 쿼리
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b9070a12-1094-44d6-bb87-a23b50bcb0af
ms.openlocfilehash: 16091f90d700dd62df0870eaf74ad46c716785d3
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504624"
---
# <a name="querying-the-datarowview-collection-in-a-dataview"></a>DataView에서 DataRowView 컬렉션 쿼리
<xref:System.Data.DataView>는 <xref:System.Data.DataRowView> 개체의 열거할 수 있는 컬렉션을 노출합니다. <xref:System.Data.DataRowView>는 <xref:System.Data.DataRow>의 사용자 지정 뷰를 나타내고 컨트롤에 해당 <xref:System.Data.DataRow>의 특정 버전을 표시합니다. <xref:System.Data.DataRow>와 같은 컨트롤을 통해서는 <xref:System.Windows.Forms.DataGridView>의 한 버전만 표시할 수 있습니다. <xref:System.Data.DataRow>의 <xref:System.Data.DataRowView> 속성을 통해 <xref:System.Data.DataRowView.Row%2A>에 의해 노출되는 <xref:System.Data.DataRowView>에 액세스할 수 있습니다. <xref:System.Data.DataRowView>를 사용하여 값을 보는 경우 <xref:System.Data.DataView.RowStateFilter%2A> 속성에 따라 원본 <xref:System.Data.DataRow>에서 노출되는 행 버전이 결정됩니다. 사용 하 여 다른 행 버전에 액세스 하는 방법에 대 한 정보에 대 한는 <xref:System.Data.DataRow>를 참조 하세요 [행 상태 및 행 버전](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)합니다. 때문에 컬렉션 <xref:System.Data.DataRowView> 에 의해 노출 되는 개체는 <xref:System.Data.DataView> 는 열거형을 사용할 수 있습니다 LINQ to DataSet 쿼리를 통해.  
  
 다음 예제에서는 `Product` 테이블에서 색상이 빨강인 제품을 쿼리하고 쿼리 결과로부터 테이블을 만듭니다. 이 테이블에서 <xref:System.Data.DataView>를 만들고, 삭제되고 수정된 행을 필터링하도록 <xref:System.Data.DataView.RowStateFilter%2A> 속성을 설정합니다. 그런 다음 LINQ 쿼리의 소스로 <xref:System.Data.DataView>를 사용하고, 수정되고 삭제된 <xref:System.Data.DataRowView> 개체를 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩합니다.  
  
 [!code-csharp[DP DataView Samples#QueryDataView2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview2)]
 [!code-vb[DP DataView Samples#QueryDataView2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview2)]  
  
 다음 예제에서는 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩된 뷰에서 제품 테이블을 만듭니다. <xref:System.Data.DataView>에서 색상이 빨강인 제품을 쿼리하고 정렬된 결과를 <xref:System.Windows.Forms.DataGridView> 컨트롤에 바인딩합니다.  
  
 [!code-csharp[DP DataView Samples#QueryDataView1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP DataView Samples/CS/Form1.cs#querydataview1)]
 [!code-vb[DP DataView Samples#QueryDataView1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP DataView Samples/VB/Form1.vb#querydataview1)]  
  
## <a name="see-also"></a>참고자료

- [데이터 바인딩 및 LINQ to DataSet](../../../../docs/framework/data/adonet/data-binding-and-linq-to-dataset.md)
