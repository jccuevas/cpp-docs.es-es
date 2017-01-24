---
title: "CWindowDC Class | Microsoft Docs"
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
  - "CWindowDC"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CWindowDC class"
  - "device contexts, ventana"
  - "screen output classes"
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
caps.latest.revision: 22
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWindowDC Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Derivada de `CDC`.  
  
## Sintaxis  
  
```  
class CWindowDC : public CDC  
```  
  
## Members  
  
### Constructores públicos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CWindowDC::CWindowDC](../Topic/CWindowDC::CWindowDC.md)|Crea un objeto `CWindowDC`.|  
  
### Miembros de datos protegidos  
  
|Nombre|Descripción|  
|------------|-----------------|  
|[CWindowDC::m\_hWnd](../Topic/CWindowDC::m_hWnd.md)|Propiedad `HWND` a la que está asociado el objeto `CWindowDC`.|  
  
## Comentarios  
 Llama a la función de Windows [GetWindowDC](http://msdn.microsoft.com/library/windows/desktop/dd144947\(v=vs.85\).aspx)en tiempo de compilación y [ReleaseDC](http://msdn.microsoft.com/library/windows/desktop/dd162920\(v=vs.85\).aspx) en tiempo de destrucción.  Esto significa que un objeto `CWindowDC` tiene acceso al área de pantalla completa de [CWnd](../../mfc/reference/cwnd-class.md) \(áreas cliente y no cliente\).  
  
 Para obtener más información sobre cómo utilizar `CWindowDC`, vea [Contextos de dispositivos](../../mfc/device-contexts.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CDC](../../mfc/reference/cdc-class.md)  
  
 `CWindowDC`  
  
## Requisitos  
 Encabezado: afxwin.h  
  
## Vea también  
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)