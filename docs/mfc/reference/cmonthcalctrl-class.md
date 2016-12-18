---
title: "CMonthCalCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMonthCalCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMonthCalCtrl class"
  - "controles comunes, Internet Explorer 4.0"
  - "Internet Explorer 4.0 common controls"
  - "month calendar controls"
  - "month calendar controls, CMonthCalCtrl class"
ms.assetid: a42f6bd6-ab5c-4335-82f8-839982fc64a2
caps.latest.revision: 23
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMonthCalCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula la funcionalidad de un control de calendario mensual.  
  
## Sintaxis  
  
```  
class CMonthCalCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::CMonthCalCtrl](../Topic/CMonthCalCtrl::CMonthCalCtrl.md)|Crea un objeto `CMonthCalCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMonthCalCtrl::Create](../Topic/CMonthCalCtrl::Create.md)|Crea un control de calendario mensual y lo asocia al objeto de `CMonthCalCtrl` .|  
|[CMonthCalCtrl::GetCalendarBorder](../Topic/CMonthCalCtrl::GetCalendarBorder.md)|Recupera el ancho del borde del control actual de calendario mensual.|  
|[CMonthCalCtrl::GetCalendarCount](../Topic/CMonthCalCtrl::GetCalendarCount.md)|Recupera el número de calendarios mostrados en el control actual de calendario mensual.|  
|[CMonthCalCtrl::GetCalendarGridInfo](../Topic/CMonthCalCtrl::GetCalendarGridInfo.md)|Información de recupera sobre el control actual de calendario mensual.|  
|[CMonthCalCtrl::GetCalID](../Topic/CMonthCalCtrl::GetCalID.md)|Recupera el identificador del calendario del control actual de calendario mensual.|  
|[CMonthCalCtrl::GetColor](../Topic/CMonthCalCtrl::GetColor.md)|Obtiene el color de un área especificada de un control de calendario mensual.|  
|[CMonthCalCtrl::GetCurrentView](../Topic/CMonthCalCtrl::GetCurrentView.md)|Recupera la vista que muestra actualmente por el control actual de calendario mensual.|  
|[CMonthCalCtrl::GetCurSel](../Topic/CMonthCalCtrl::GetCurSel.md)|Recupera la hora del sistema tal como indica la fecha actualmente seleccionados.|  
|[CMonthCalCtrl::GetFirstDayOfWeek](../Topic/CMonthCalCtrl::GetFirstDayOfWeek.md)|Obtiene el primer día de la semana que se mostrará en la columna situada más a la izquierda del calendario.|  
|[CMonthCalCtrl::GetMaxSelCount](../Topic/CMonthCalCtrl::GetMaxSelCount.md)|Recupera el número máximo actual de días que puedan ser seleccionado en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMaxTodayWidth](../Topic/CMonthCalCtrl::GetMaxTodayWidth.md)|Recupera el ancho máximo de la cadena de “Today” del control actual de calendario mensual.|  
|[CMonthCalCtrl::GetMinReqRect](../Topic/CMonthCalCtrl::GetMinReqRect.md)|Recupera el tamaño mínimo necesario para mostrar un mes completo en un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthDelta](../Topic/CMonthCalCtrl::GetMonthDelta.md)|Recupera la tasa de desplazamiento de un control de calendario mensual.|  
|[CMonthCalCtrl::GetMonthRange](../Topic/CMonthCalCtrl::GetMonthRange.md)|Información de fecha de recupera que representa los límites del máximo y mínimo de la presentación de un control de calendario mensual.|  
|[CMonthCalCtrl::GetRange](../Topic/CMonthCalCtrl::GetRange.md)|Recupera el mínimo actual y las fechas finales establecidos en un control de calendario mensual.|  
|[CMonthCalCtrl::GetSelRange](../Topic/CMonthCalCtrl::GetSelRange.md)|Información de fecha de recupera que representa los límites superior e inferior del intervalo de fechas actualmente seleccionado por el usuario.|  
|[CMonthCalCtrl::GetToday](../Topic/CMonthCalCtrl::GetToday.md)|Recupera información de fecha para la fecha especificada como “actual” para un control de calendario mensual.|  
|[CMonthCalCtrl::HitTest](../Topic/CMonthCalCtrl::HitTest.md)|Determina que la sección de un control de calendario mensual es en un punto determinado de la pantalla.|  
|[CMonthCalCtrl::IsCenturyView](../Topic/CMonthCalCtrl::IsCenturyView.md)|Indica si la vista actual del control actual de calendario mensual es la vista del siglo.|  
|[CMonthCalCtrl::IsDecadeView](../Topic/CMonthCalCtrl::IsDecadeView.md)|Indica si la vista actual del control actual de calendario mensual es la vista de década.|  
|[CMonthCalCtrl::IsMonthView](../Topic/CMonthCalCtrl::IsMonthView.md)|Indica si la vista actual del control actual de calendario mensual es la vista del mes.|  
|[CMonthCalCtrl::IsYearView](../Topic/CMonthCalCtrl::IsYearView.md)|Indica si la vista actual del control actual de calendario mensual es la vista del año.|  
|[CMonthCalCtrl::SetCalendarBorder](../Topic/CMonthCalCtrl::SetCalendarBorder.md)|Establece el ancho del borde del control actual de calendario mensual.|  
|[CMonthCalCtrl::SetCalendarBorderDefault](../Topic/CMonthCalCtrl::SetCalendarBorderDefault.md)|Establece el ancho predeterminado del borde del control actual de calendario mensual.|  
|[CMonthCalCtrl::SetCalID](../Topic/CMonthCalCtrl::SetCalID.md)|Establece el identificador del calendario del control actual de calendario mensual.|  
|[CMonthCalCtrl::SetCenturyView](../Topic/CMonthCalCtrl::SetCenturyView.md)|Establece el control actual de calendario mensual para mostrar la vista del siglo.|  
|[CMonthCalCtrl::SetColor](../Topic/CMonthCalCtrl::SetColor.md)|Establece el color de un área especificada de un control de calendario mensual.|  
|[CMonthCalCtrl::SetCurrentView](../Topic/CMonthCalCtrl::SetCurrentView.md)|Establece el control actual de calendario mensual para mostrar la vista especificada.|  
|[CMonthCalCtrl::SetCurSel](../Topic/CMonthCalCtrl::SetCurSel.md)|Establece la fecha actualmente seleccionado para un control de calendario mensual.|  
|[CMonthCalCtrl::SetDayState](../Topic/CMonthCalCtrl::SetDayState.md)|Establece la presentación para los días en un control de calendario mensual.|  
|[CMonthCalCtrl::SetDecadeView](../Topic/CMonthCalCtrl::SetDecadeView.md)|Establece el control actual de calendario mensual a la vista de década.|  
|[CMonthCalCtrl::SetFirstDayOfWeek](../Topic/CMonthCalCtrl::SetFirstDayOfWeek.md)|Establece el día de semana que se mostrará en la columna situada más a la izquierda del calendario.|  
|[CMonthCalCtrl::SetMaxSelCount](../Topic/CMonthCalCtrl::SetMaxSelCount.md)|Establece el número máximo de días que puedan ser seleccionado en un control de calendario mensual.|  
|[CMonthCalCtrl::SetMonthDelta](../Topic/CMonthCalCtrl::SetMonthDelta.md)|Establece la tasa de desplazamiento de un control de calendario mensual.|  
|[CMonthCalCtrl::SetMonthView](../Topic/CMonthCalCtrl::SetMonthView.md)|Establece el control actual de calendario mensual para mostrar la vista del mes.|  
|[CMonthCalCtrl::SetRange](../Topic/CMonthCalCtrl::SetRange.md)|Establece el mínimo y fechas con un tiempo máximo para un control de calendario mensual.|  
|[CMonthCalCtrl::SetSelRange](../Topic/CMonthCalCtrl::SetSelRange.md)|Establece la selección en un control de calendario mensual a un intervalo de fechas determinado.|  
|[CMonthCalCtrl::SetToday](../Topic/CMonthCalCtrl::SetToday.md)|Establece el control de calendario para el día actual.|  
|[CMonthCalCtrl::SetYearView](../Topic/CMonthCalCtrl::SetYearView.md)|Establece el control actual de calendario mensual a la vista del año.|  
|[CMonthCalCtrl::SizeMinReq](../Topic/CMonthCalCtrl::SizeMinReq.md)|Redibuja el control de calendario mensual al tamaño mínimo, un mes.|  
|[CMonthCalCtrl::SizeRectToMin](../Topic/CMonthCalCtrl::SizeRectToMin.md)|Para el control actual de calendario mensual, calcula el rectángulo más pequeño que puede contener todos los calendarios que caben en un rectángulo especificado.|  
  
## Comentarios  
 El control de calendario mensual proporciona al usuario una interfaz simple de calendario, que el usuario puede seleccionar una fecha.  El usuario puede cambiar la presentación por:  
  
-   El desplazamiento hacia atrás y reenvía, de un mes a otro.  
  
-   Haciendo clic en el Today text para mostrar el día \(si el estilo de **MCS\_NOTODAY** no se utiliza\).  
  
-   Elegir un mes o año de un menú emergente.  
  
 Puede personalizar el control de calendario mensual aplicando una variedad de estilos al objeto cuando lo crea.  estos estilos se describen en [Estilos del Control de calendario mensual](http://msdn.microsoft.com/library/windows/desktop/bb760919) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)].  
  
 El control de calendario mensual puede mostrar más de un mes, y puede indicar días especiales \(como vacaciones\) por en negrita la fecha.  
  
 Para obtener más información sobre cómo utilizar el control de calendario mensual, vea [Mediante CMonthCalCtrl](../../mfc/using-cmonthcalctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CMonthCalCtrl`  
  
## Requisitos  
 **encabezado:** afxdtctl.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDateTimeCtrl Class](../../mfc/reference/cdatetimectrl-class.md)