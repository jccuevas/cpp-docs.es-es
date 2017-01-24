---
title: "CClientDC Class | Microsoft Docs"
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
  - "CClientDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CClientDC class"
  - "CDC (clase), device contexts for client areas"
  - "client-area device context"
  - "device contexts, área de cliente"
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CClientDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se encarga de llamar a funciones de Windows [GetDC](http://msdn.microsoft.com/library/windows/desktop/dd144871) en tiempo de construcción y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920) en tiempo de destrucción.  
  
## Sintaxis  
  
```  
  
class CClientDC : public CDC  
  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CClientDC::CClientDC](../Topic/CClientDC::CClientDC.md)|Construye un objeto de `CClientDC` conectado a `CWnd`.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CClientDC::m\_hWnd](../Topic/CClientDC::m_hWnd.md)|`HWND` de la ventana para la que este `CClientDC` es válido.|  
  
## Comentarios  
 Esto significa que el contexto de dispositivo asociado con un objeto de `CClientDC` es el área cliente de una ventana.  
  
 Para obtener más información sobre `CClientDC`, vea [Contextos de dispositivo](../../mfc/device-contexts.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CClientDC`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)