---
title: "CAxWindow Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CAxWindowT"
  - "CAxWindow"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, hospedar controles ActiveX"
  - "CAxWindow class"
ms.assetid: 85e79261-43e4-4770-bde0-1ff87f222b0f
caps.latest.revision: 24
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CAxWindow Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden utilizar en las aplicaciones que se ejecutan en Windows en tiempo de ejecución.  
  
## Sintaxis  
  
```  
  
class CAxWindow : public CWindow  
  
```  
  
## Members  
  
### Métodos  
  
|||  
|-|-|  
|[AttachControl](../Topic/CAxWindow::AttachControl.md)|Asocia un control ActiveX existente al objeto de `CAxWindow` .|  
|[CAxWindow](../Topic/CAxWindow::CAxWindow.md)|Crea un objeto `CAxWindow`.|  
|[CreateControl](../Topic/CAxWindow::CreateControl.md)|Crea un control ActiveX, se inicializa, y los hospedarlo en la ventana de `CAxWindow` .|  
|[CreateControlEx](../Topic/CAxWindow::CreateControlEx.md)|Crea un control ActiveX y recupera un puntero de interfaz \(o a punteros\) del control.|  
|[GetWndClassName](../Topic/CAxWindow::GetWndClassName.md)|\(Estático\) recupera el nombre de clase predefinido del objeto de `CAxWindow` .|  
|[QueryControl](../Topic/CAxWindow::QueryControl.md)|Recupera **IUnknown** de controles ActiveX hospedado.|  
|[QueryHost](../Topic/CAxWindow::QueryHost.md)|Recupera el puntero de **IUnknown** del objeto de `CAxWindow` .|  
|[SetExternalDispatch](../Topic/CAxWindow::SetExternalDispatch.md)|Establece la interfaz de envío externa utilizada por el objeto de `CAxWindow` .|  
|[SetExternalUIHandler](../Topic/CAxWindow::SetExternalUIHandler.md)|Establece la interfaz de **IDocHostUIHandler** externo utilizada por el objeto de `CAxWindow` .|  
  
### Operadores  
  
|||  
|-|-|  
|[operador \=](../Topic/CAxWindow::operator%20=.md)|Asigna **HWND** a un objeto existente de**CAxWindow** .|  
  
## Comentarios  
 Esta clase proporciona métodos para manipular una ventana que hospeda un control ActiveX.  El hospedaje proporcionado por “**AtlAxWin80”**, que es ajustará en `CAxWindow`.  
  
 La clase `CAxWindow` se implementa como una especialización de la clase de `CAxWindowT` .  se declara esta especialización como:  
  
 `typedef CAxWindowT<CWindow> CAxWindow;`  
  
 Si necesita cambiar la clase base, puede utilizar `CAxWindowT` y especificar la nueva clase base como argumento de plantilla.  
  
## Requisitos  
 **encabezado:** atlwin.h  
  
## Vea también  
 [Ejemplo ATLCON](../../top/visual-cpp-samples.md)   
 [CWindow Class](../../atl/reference/cwindow-class.md)   
 [Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)   
 [Class Overview](../../atl/atl-class-overview.md)   
 [Preguntas más frecuentes sobre contención de controles](../../atl/atl-control-containment-faq.md)