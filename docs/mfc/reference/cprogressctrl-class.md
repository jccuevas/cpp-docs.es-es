---
title: "CProgressCtrl Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CProgressCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CProgressCtrl class"
  - "Internet Explorer 4.0 common controls"
  - "progress controls [C++], CProgressCtrl class"
ms.assetid: 222630f4-1598-4026-8198-51649b1192ab
caps.latest.revision: 25
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 26
---
# CProgressCtrl Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona la funcionalidad de controles comunes de la barra de progreso de Windows.  
  
## Sintaxis  
  
```  
class CProgressCtrl : public CWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CProgressCtrl::CProgressCtrl](../Topic/CProgressCtrl::CProgressCtrl.md)|Crea un objeto `CProgressCtrl`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)|Crea un control de barra de progreso y lo asocia a un objeto de `CProgressCtrl` .|  
|[CProgressCtrl::CreateEx](../Topic/CProgressCtrl::CreateEx.md)|Crea un control de progreso con Windows especificado extendidas estilos y lo asocia a un objeto de `CProgressCtrl` .|  
|[CProgressCtrl::GetBarColor](../Topic/CProgressCtrl::GetBarColor.md)|Obtiene el color de la barra del indicador de progreso para el control actual de barra de progreso.|  
|[CProgressCtrl::GetBkColor](../Topic/CProgressCtrl::GetBkColor.md)|Obtiene el color de fondo de la barra de progreso actual.|  
|[CProgressCtrl::GetPos](../Topic/CProgressCtrl::GetPos.md)|Obtiene la posición actual de la barra de progreso.|  
|[CProgressCtrl::GetRange](../Topic/CProgressCtrl::GetRange.md)|Obtiene los límites superior e inferior del intervalo del control de barra de progreso.|  
|[CProgressCtrl::GetState](../Topic/CProgressCtrl::GetState.md)|Obtiene el estado del control actual de barra de progreso.|  
|[CProgressCtrl::GetStep](../Topic/CProgressCtrl::GetStep.md)|Recupera el incremento del paso de la barra de progreso del control actual de barra de progreso.|  
|[CProgressCtrl::OffsetPos](../Topic/CProgressCtrl::OffsetPos.md)|Avanza la posición actual de un control de barra de progreso en un incremento especificado y redibuja la barra para reflejar la nueva posición.|  
|[CProgressCtrl::SetBarColor](../Topic/CProgressCtrl::SetBarColor.md)|Establece el color de la barra del indicador de progreso en el control actual de barra de progreso.|  
|[CProgressCtrl::SetBkColor](../Topic/CProgressCtrl::SetBkColor.md)|establece el color de fondo para la barra de progreso.|  
|[CProgressCtrl::SetMarquee](../Topic/CProgressCtrl::SetMarquee.md)|Activa el modo de la marquesina con o. para el control actual de barra de progreso.|  
|[CProgressCtrl::SetPos](../Topic/CProgressCtrl::SetPos.md)|Establece la posición actual para un control de barra de progreso y redibuja la barra para reflejar la nueva posición.|  
|[CProgressCtrl::SetRange](../Topic/CProgressCtrl::SetRange.md)|Establece los intervalos mínimos y máximos para un control de barra de progreso y redibuja la barra para reflejar los nuevos intervalos.|  
|[CProgressCtrl::SetState](../Topic/CProgressCtrl::SetState.md)|Establece el estado del control actual de barra de progreso.|  
|[CProgressCtrl::SetStep](../Topic/CProgressCtrl::SetStep.md)|Especifica el incremento de paso para un control de barra de progreso.|  
|[CProgressCtrl::StepIt](../Topic/CProgressCtrl::StepIt.md)|Avanza la posición actual para un control de barra de progreso en el incremento de paso \(vea [SetStep](../Topic/CProgressCtrl::SetStep.md)\) y redibuja la barra para reflejar la nueva posición.|  
  
## Comentarios  
 Un control de barra de progreso es una ventana que una aplicación puede utilizar para indicar el progreso de una operación larga.  Está compuesto de un rectángulo que se llena gradualmente, de izquierda a derecha, con el color de resaltado del sistema a medida que una operación progresa.  
  
 Un control de barra de progreso tiene un intervalo y una posición actual.  El intervalo representa la duración total de la operación, y la posición actual representa el progreso que la aplicación ha creado para completar la operación.  El procedimiento de ventana utiliza el intervalo y la posición actual para determinar el porcentaje de la barra de progreso para rellenar con el resaltado color.  Dado que los valores de intervalo y de la posición actual se expresan como enteros con signo, el intervalo posible de los valores de la posición actual es \(de 2.147.483.648 a 2.147.483.647 inclusive.  
  
 Para obtener más información sobre cómo utilizar `CProgressCtrl`, vea [Controles](../../mfc/controls-mfc.md) y [Mediante CProgressCtrl](../../mfc/using-cprogressctrl.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 `CProgressCtrl`  
  
## Requisitos  
 **encabezado:** afxcmn.h  
  
## Vea también  
 [ejemplo CMNCTRL2 de MFC](../../top/visual-cpp-samples.md)   
 [CWnd \(clase\)](../../mfc/reference/cwnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)