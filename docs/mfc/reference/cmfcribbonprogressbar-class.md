---
title: "CMFCRibbonProgressBar Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCRibbonProgressBar"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCRibbonProgressBar class"
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCRibbonProgressBar Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa un control que indique visualmente el progreso de una operación larga.  
  
## Sintaxis  
  
```  
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](../Topic/CMFCRibbonProgressBar::CMFCRibbonProgressBar.md)|Las construcciones e inicializan un objeto de `CMFCRibbonProgressBar` .|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCRibbonProgressBar::GetPos](../Topic/CMFCRibbonProgressBar::GetPos.md)|devuelve el progreso actual.|  
|[CMFCRibbonProgressBar::GetRangeMax](../Topic/CMFCRibbonProgressBar::GetRangeMax.md)|Devuelve el valor máximo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRangeMin](../Topic/CMFCRibbonProgressBar::GetRangeMin.md)|Devuelve el valor mínimo del intervalo actual.|  
|[CMFCRibbonProgressBar::GetRegularSize](../Topic/CMFCRibbonProgressBar::GetRegularSize.md)|Devuelve el tamaño normal del elemento cinta.  \(Reemplaza [CMFCRibbonBaseElement::GetRegularSize](../Topic/CMFCRibbonBaseElement::GetRegularSize.md).\)|  
|[CMFCRibbonProgressBar::IsInfiniteMode](../Topic/CMFCRibbonProgressBar::IsInfiniteMode.md)|Especifica si la barra de progreso funciona en modo infinito.|  
|[CMFCRibbonProgressBar::OnDraw](../Topic/CMFCRibbonProgressBar::OnDraw.md)|Llamado por el marco para dibujar el elemento cinta.  \(Reemplaza [CMFCRibbonBaseElement::OnDraw](../Topic/CMFCRibbonBaseElement::OnDraw.md).\)|  
|[CMFCRibbonProgressBar::SetInfiniteMode](../Topic/CMFCRibbonProgressBar::SetInfiniteMode.md)|Establece la barra de progreso para ejecutarse en modo infinito.|  
|[CMFCRibbonProgressBar::SetPos](../Topic/CMFCRibbonProgressBar::SetPos.md)|establece el progreso actual.|  
|[CMFCRibbonProgressBar::SetRange](../Topic/CMFCRibbonProgressBar::SetRange.md)|Establece los valores mínimo y máximo.|  
  
## Comentarios  
 `CMFCRibbonProgressBar` puede funcionar en dos modos: regular e infinito.  En modo normal, la barra de progreso se rellena de izquierda a derecha y se detiene cuando alcanza el valor máximo.  En modo infinito, barra de progreso se rellena repetidamente desde el valor mínimo al valor máximo.  Puede utilizar el modo infinito para indicar que una operación está en curso, pero que el tiempo de finalización es desconocido.  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar varios métodos en la clase de `CMFCRibbonProgressBar` .  El ejemplo muestra cómo establecer la barra de progreso para ejecutarse en modo infinito \(donde es desconocida la hora de finalización de una operación\), establece los valores mínimo y máximo de la barra de progreso, y establece la posición actual de la barra de progreso.  Este fragmento de código es parte de [Ejemplo 2007 de demostración de MS Office](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/CPP/cmfcribbonprogressbar-class_1.cpp)]  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)  
  
 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)  
  
## Requisitos  
 **encabezado:** afxRibbonProgressBar.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCRibbonBaseElement Class](../../mfc/reference/cmfcribbonbaseelement-class.md)   
 [CMFCRibbonBar Class](../../mfc/reference/cmfcribbonbar-class.md)