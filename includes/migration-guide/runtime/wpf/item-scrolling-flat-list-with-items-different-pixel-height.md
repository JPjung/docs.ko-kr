---
ms.openlocfilehash: eb3cfdfd39444536f423b65166a3413db67a0e01
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802967"
---
### <a name="item-scrolling-a-flat-list-with-items-of-different-pixel-height"></a>픽셀 높이가 다른 항목을 포함하는 단순 목록 항목 스크롤

|   |   |
|---|---|
|세부 정보|<xref:System.Windows.Controls.ItemsControl?displayProperty=name>이 가상화(<code>IsVirtualizing=true</code>) 및 항목 스크롤(<code>ScrollUnit=Item</code>)을 사용하여 컬렉션을 표시하고 해당 높이(픽셀)가 인접 항목과 다른 항목을 표시하기 위해 컨트롤이 스크롤되는 경우 <xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=name>은 컬렉션의 모든 항목을 반복합니다. 이 반복에서 UI가 응답하지 않습니다. 컬렉션이 대규모인 경우 중단으로 감지될 수 있습니다. 반복은 이전 .NET Framework 릴리스 등 다른 상황에서도 발생합니다. 예를 들어 픽셀 높이가 다른 항목이 나타나는 경우 픽셀 스크롤할 때(<code>ScrollUnit=Pixel</code>) 및 하위 항목 수가 인접 항목과 다른 항목이 나타나는 경우 계층적 데이터를 항목 스크롤할 때(예: 그룹화가 사용되는 <xref:System.Windows.Controls.TreeView?displayProperty=name> 또는 <xref:System.Windows.Controls.ItemsControl?displayProperty=name>) 발생합니다. 항목 스크롤을 사용하고 픽셀 높이가 다른 경우 계층 구조 데이터의 레이아웃에서 버그를 수정하기 위해 .NET Framework 4.6.1에 반복이 도입되었습니다.  데이터가 단일 구조(계층 구조 아님)인 경우 반복이 필요하지 않으며 이 경우 .NET Framework 4.6.2가 반복을 수행하지 않습니다.|
|제안 해결 방법|반복이 .NET Framework 4.6.1에서 발생하지만 이전 릴리스에서는 발생하지 않는 경우, 즉, <xref:System.Windows.Controls.ItemsControl?displayProperty=name>이 항목의 픽셀 높이가 서로 다른 항목의 단순 목록을 항목 스크롤하는 경우 다음과 같은 두 가지 방법으로 해결할 수 있습니다.<ol><li>.NET Framework 4.6.2를 설치합니다.</li><li>.NET Framework 4.6.1용 핫픽스 HR 1605를 설치합니다.</li></ol>|
|범위|부|
|버전|4.6.1|
|형식|런타임|
|영향을 받는 API|<ul><li><xref:System.Windows.Controls.VirtualizingStackPanel?displayProperty=nameWithType></li></ul>|

