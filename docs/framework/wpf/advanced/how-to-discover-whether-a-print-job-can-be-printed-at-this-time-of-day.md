---
title: '방법: 특정 시간에 인쇄 작업을 인쇄할 수 있는지 확인'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print queues [WPF], timing
- printers [WPF], availability
- print jobs [WPF], timing
ms.assetid: 7e9c8ec1-abf6-4b3d-b1c6-33b35d3c4063
ms.openlocfilehash: ee38caedc5d5a29d2221d6e5a6bf6cf74617bf8c
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859713"
---
# <a name="how-to-discover-whether-a-print-job-can-be-printed-at-this-time-of-day"></a>방법: 특정 시간에 인쇄 작업을 인쇄할 수 있는지 확인
인쇄 대기열 항상 사용할 수 없는 하루 24 시간에 대 한 합니다. 하루 중 특정 시간에 사용할 수 없도록 설정할 수 있는 시작 및 종료 시간 속성을 갖습니다. 예를 들어, 오후 5 시 이후에 특정 부서 에서만 단독으로 사용에 대 한 프린터를 예약 합니다.이 기능은 사용할 수 있습니다. 해당 학과 사용 되는 다른 큐에서는 다른 부서에서 프린터를 처리 해야 합니다. 선호 하는 방식된 부서에 대 한 큐 수를 설정할 수 있지만 항상 사용 가능한, 다른 부서에 대 한 큐 오후 5 시 이후에 사용할 수 없게 설정할 수 됩니다.  
  
 또한 인쇄 작업 자체는 지정 된 기간 내 에서만 인쇄 가능 하도록 설정할 수 있습니다.  
  
 합니다 <xref:System.Printing.PrintQueue> 고 <xref:System.Printing.PrintSystemJobInfo> Api의 Microsoft.NET Framework에 노출 하는 클래스 원격으로 현재 시간에 지정 된 큐에 지정된 된 인쇄 작업을 인쇄할 수 있는지를 확인 하기 위한 수단을 제공 합니다.  
  
## <a name="example"></a>예제  
 아래 예제에는 인쇄 작업 문제를 진단할 수 있는 샘플입니다.  
  
 이러한 종류의 함수에 대 한 두 가지 주요 단계는 다음과 같습니다.  
  
1. 읽기를 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 및 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 의 속성을 <xref:System.Printing.PrintQueue> 현재 시간 사이 인지 여부를 확인 합니다.  
  
2. 읽기를 <xref:System.Printing.PrintSystemJobInfo.StartTimeOfDay%2A> 및 <xref:System.Printing.PrintSystemJobInfo.UntilTimeOfDay%2A> 의 속성을 <xref:System.Printing.PrintSystemJobInfo> 현재 시간 사이 인지 여부를 확인 합니다.  
  
 이러한 속성은 한다는 사실에서 문제가 발생 하지만 <xref:System.DateTime> 개체입니다. 대신 이들은 <xref:System.Int32> 자정 이후의 시간 (분) 수와 시간을 나타내는 개체입니다. 또한이 아닌 경우 자정 현재 표준 시간대, UTC (협정 세계시) 자정에  
  
 첫 번째 코드 예제에서는 정적 메서드를 제공 **ReportQueueAndJobAvailability**, 전달 되는 <xref:System.Printing.PrintSystemJobInfo> 작업을 현재 인쇄할 수 있는지 여부를 확인 하는 도우미 메서드를 호출 하 고, 그렇지 않은 경우 인쇄할 수 있는 경우. 에 <xref:System.Printing.PrintQueue> 메서드에 전달 되지 않습니다. 때문에 이것이 합니다 <xref:System.Printing.PrintSystemJobInfo> 큐에 대 한 참조를 포함 합니다. 해당 <xref:System.Printing.PrintSystemJobInfo.HostingPrintQueue%2A> 속성입니다.  
  
 하위 메서드 오버 로드 된 포함 **ReportAvailabilityAtThisTime** 중 하나를 수행 하는 메서드를 <xref:System.Printing.PrintQueue> 또는 <xref:System.Printing.PrintSystemJobInfo> 매개 변수로 합니다. 이기도 한 **TimeConverter.ConvertToLocalHumanReadableTime**합니다. 이러한 모든 메서드는 아래 설명 되어 있습니다.  
  
 합니다 **ReportQueueAndJobAvailability** 메서드를 확인 하는 경우 큐 나 인쇄 작업에 사용할 수 없는이 이번 하 여 시작 합니다. 둘 중 하나를 사용할 수 없는 경우 다음 확인 하는 경우 사용할 수 없는 큐입니다. 사용할 수 없는 경우이 팩트 및 경우 큐가 다시 사용할 수 있게 하는 경우 메서드를 보고 합니다. 그런 다음 작업을 확인 하 고 다음에 사용할 수 없는 경우 보고 될 때 범위 인쇄할 수 있는 경우. 마지막으로 메서드 작업을 인쇄할 수 때 가장 이른 시간을 보고 합니다. 이 다음 두 번 이상입니다.  
  
- 인쇄 큐가 사용할 수 있는 다음 시간입니다.  
  
- 인쇄 작업을 사용할 다음 시간입니다.  
  
 하루 중 시간을 보고할 때는 <xref:System.DateTime.ToShortTimeString%2A> 메서드 호출 년, 월 및 일 출력에서이 메서드를 표시 하지 않습니다. 특정 연도, 월 또는 일 하는 인쇄 대기열 또는 인쇄 작업의 가용성을 제한할 수 없습니다.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#reportqueueandjobavailability)]
 [!code-csharp[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#reportqueueandjobavailability)]
 [!code-vb[DiagnoseProblematicPrintJob#ReportQueueAndJobAvailability](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#reportqueueandjobavailability)]  
  
 두 오버 로드는 **ReportAvailabilityAtThisTime** 되므로 전달 된 형식을 제외 하 고는 것과 동일 합니다 <xref:System.Printing.PrintQueue> 버전은 아래 표시 됩니다.  
  
> [!NOTE]
>  메서드는 형식을 제외 하 고 동일한 샘플 제네릭 메서드를 만들지 않으므로 이유에 대 한 문제를 발생 시킵니다 **ReportAvailabilityAtThisTime\<T >** 합니다. 이러한 메서드는 있는 클래스로 사용할 수 있는 이유는 합니다 **StartTimeOfDay** 하 고 **UntilTimeOfDay** 메서드를 호출 하는 속성 이지만 제네릭 메서드만 제한할 수 있습니다를 단일 클래스 및 둘 다에 공통적인 유일한 클래스 <xref:System.Printing.PrintQueue> 하 고 <xref:System.Printing.PrintSystemJobInfo> 상속 트리는 <xref:System.Printing.PrintSystemObject> 는 이러한 속성이 없습니다.  
  
 합니다 **ReportAvailabilityAtThisTime** (아래 코드 예제에 표시) 하는 메서드를 초기화 하 여 시작을 <xref:System.Boolean> sentinel 변수 `true`합니다. 다시 설정 됩니다 `false`이면 큐를 사용할 수 없습니다.  
  
 메서드가 있는지를 확인 하는 다음으로, 시작 및 "until" 시간은 동일 합니다. 메서드가 반환 되므로 큐가 사용 가능한 항상 경우 `true`합니다.  
  
 정적 메서드를 사용 하 여 큐를 사용할 수 없는 경우 항상, <xref:System.DateTime.UtcNow%2A> 현재 시간을 가져올 속성을 <xref:System.DateTime> 개체입니다. (때문에 현지 시간 필요 하지 않습니다 합니다 <xref:System.Printing.PrintQueue.StartTimeOfDay%2A> 및 <xref:System.Printing.PrintQueue.UntilTimeOfDay%2A> 속성은 그 자체가 UTC 시간에서입니다.)  
  
 그러나 이러한 두 속성은 <xref:System.DateTime> 개체입니다. 이들은 <xref:System.Int32>의분 후 UTC 자정 숫자로 시간을 표현 합니다. 변환할 필요가 있으므로 <xref:System.DateTime> 개체 자정 이후의 분입니다. 완료 되 면 메서드는 큐의 시작 사이의 "시간 집합 센티널 false 경우"지금 "을이 두 시간 사이 없는 및 반환 된 sentinel until"은 "now" 여부를 확인 하려면 확인 하기만 하면 됩니다.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#printqueuestartuntil)]
 [!code-csharp[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#printqueuestartuntil)]
 [!code-vb[DiagnoseProblematicPrintJob#PrintQueueStartUntil](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#printqueuestartuntil)]  
  
 합니다 **TimeConverter.ConvertToLocalHumanReadableTime** 메서드 (아래 코드 예제에 표시) 토론에 대 한 간략 한 이므로 Microsoft.NET Framework를 사용 하 여 도입 된 메서드를 사용 하지 않습니다. Double 변환 작업 메서드가: 자정 이후의 분을 나타내는 정수를 사용 하 고 사용자를 읽을 수 있는 시간으로 변환 하 고이 현지 시간으로 변환 해야 합니다. 처음 생성 하 여이 작업을 수행 하는 <xref:System.DateTime> UTC 다음 변수를 사용 하는 자정으로 설정 된 개체는 <xref:System.DateTime.AddMinutes%2A> 메서드에 전달 된 분을 추가 하는 방법입니다. 이 반환 된 새 <xref:System.DateTime> 메서드에 전달 된 원래 시간을 표현 합니다. <xref:System.DateTime.ToLocalTime%2A> 메서드 다음이 현지 시간으로 변환 합니다.  
  
 [!code-cpp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/cpp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CPP/Program.cpp#timeconverter)]
 [!code-csharp[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/csharp/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/CSharp/Program.cs#timeconverter)]
 [!code-vb[DiagnoseProblematicPrintJob#TimeConverter](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DiagnoseProblematicPrintJob/visualbasic/program.vb#timeconverter)]  
  
## <a name="see-also"></a>참고자료

- <xref:System.DateTime>
- <xref:System.Printing.PrintSystemJobInfo>
- <xref:System.Printing.PrintQueue>
- [WPF의 문서](documents-in-wpf.md)
- [인쇄 개요](printing-overview.md)
