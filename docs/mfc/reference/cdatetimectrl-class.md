---
title: "CDateTimeCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CDateTimeCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CDateTimeCtrl class"
  - "date-picking functionality"
  - "DateTimePicker control [MFC]"
  - "DateTimePicker control [MFC], CDateTimeCtrl class"
ms.assetid: 7113993b-5d37-4148-939f-500a190c5bdc
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 24
---
# CDateTimeCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula la funcionalidad de un control de selector de fecha y hora.  
  
## Sintaxis  
  
```  
class CDateTimeCtrl : public CWnd  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDateTimeCtrl::CDateTimeCtrl](../Topic/CDateTimeCtrl::CDateTimeCtrl.md)|Crea un objeto `CDateTimeCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDateTimeCtrl::CloseMonthCal](../Topic/CDateTimeCtrl::CloseMonthCal.md)|Cierre el control actual de selector de fecha y hora.|  
|[CDateTimeCtrl::Create](../Topic/CDateTimeCtrl::Create.md)|Crea un control de selector de fecha y hora y lo asocia al objeto de `CDateTimeCtrl` .|  
|[CDateTimeCtrl::GetDateTimePickerInfo](../Topic/CDateTimeCtrl::GetDateTimePickerInfo.md)|Información de recupera sobre el control actual de selector de fecha y hora.|  
|[CDateTimeCtrl::GetIdealSize](../Topic/CDateTimeCtrl::GetIdealSize.md)|Devuelve el tamaño ideal de control selector de fecha y hora que se requiere para mostrar la fecha u hora actuales.|  
|[CDateTimeCtrl::GetMonthCalColor](../Topic/CDateTimeCtrl::GetMonthCalColor.md)|Recupera color por una parte determinada de calendario mensual dentro del control de selector de fecha y hora.|  
|[CDateTimeCtrl::GetMonthCalCtrl](../Topic/CDateTimeCtrl::GetMonthCalCtrl.md)|Recupera el objeto de `CMonthCalCtrl` asociado al control selector de fecha y hora.|  
|[CDateTimeCtrl::GetMonthCalFont](../Topic/CDateTimeCtrl::GetMonthCalFont.md)|Recuperar la fuente utilizada actualmente por el control secundario del calendario del mes de la fecha y hora de control selector.|  
|[CDateTimeCtrl::GetMonthCalStyle](../Topic/CDateTimeCtrl::GetMonthCalStyle.md)|Obtiene el estilo del control actual de selector de fecha y hora.|  
|[CDateTimeCtrl::GetRange](../Topic/CDateTimeCtrl::GetRange.md)|Recupera el mínimo actual y las horas del sistema con un tiempo máximo para un control de selector de fecha y hora.|  
|[CDateTimeCtrl::GetTime](../Topic/CDateTimeCtrl::GetTime.md)|Recupera el tiempo actualmente seleccionado en un control de selector de fecha y hora y lo coloca en una estructura especificada de `SYSTEMTIME` .|  
|[CDateTimeCtrl::SetFormat](../Topic/CDateTimeCtrl::SetFormat.md)|Establece la presentación de un control de selector de fecha y hora de acuerdo con una cadena de formato.|  
|[CDateTimeCtrl::SetMonthCalColor](../Topic/CDateTimeCtrl::SetMonthCalColor.md)|Establece el color de una parte determinada de calendario mensual dentro de un control de selector de fecha y hora.|  
|[CDateTimeCtrl::SetMonthCalFont](../Topic/CDateTimeCtrl::SetMonthCalFont.md)|Establece la fuente que el control secundario del calendario del mes de la fecha y hora de control selector utilizará.|  
|[CDateTimeCtrl::SetMonthCalStyle](../Topic/CDateTimeCtrl::SetMonthCalStyle.md)|Establece el estilo del control actual de selector de fecha y hora.|  
|[CDateTimeCtrl::SetRange](../Topic/CDateTimeCtrl::SetRange.md)|Establece el mínimo y las horas del sistema con un tiempo máximo para un control de selector de fecha y hora.|  
|[CDateTimeCtrl::SetTime](../Topic/CDateTimeCtrl::SetTime.md)|Establece el tiempo en un control de selector de fecha y hora.|  
  
## Comentarios  
 El control selector de fecha y hora \(control de DTP\) proporciona una interfaz simple para intercambiar información de fecha y hora con un usuario.  Esta interfaz contiene campos, que muestra una parte de la información de fecha y hora almacenada en el control.  El usuario puede cambiar la información almacenada en el control cambiando el contenido de la cadena en un campo determinado.  El usuario puede mover campo Del campo utilizando el mouse o el teclado.  
  
 Puede personalizar el control selector de fecha y hora aplicando una variedad de estilos al objeto cuando lo crea.  Vea [Estilos de Control de selector de fecha y hora](http://msdn.microsoft.com/library/windows/desktop/bb761728) en [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] para obtener más información sobre los estilos específicos del control selector de fecha y hora.  Puede establecer el tamaño de representación del control de DTP mediante estilos de formato.  Estos estilos de formato se describen en “formato diseñados” en el tema [Estilos de Control de selector de fecha y hora](http://msdn.microsoft.com/library/windows/desktop/bb761728)de [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] .  
  
 El control selector de fecha y hora también utiliza las notificaciones y devoluciones, que se describen en [Mediante CDateTimeCtrl](../../mfc/using-cdatetimectrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CDateTimeCtrl`  
  
## Requisitos  
 **encabezado:** afxdtctl.h  
  
## Vea también  
 [ejemplo CMNCTRL1 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CMonthCalCtrl Class](../../mfc/reference/cmonthcalctrl-class.md)