---
title: "CMiniFrameWnd Class | Microsoft Docs"
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
  - "CMiniFrameWnd"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMiniFrameWnd class"
  - "mini-frame windows"
  - "barras de herramientas [C++]"
ms.assetid: b8f534ed-0532-4d8e-9657-5595cf677749
caps.latest.revision: 21
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMiniFrameWnd Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Representa una ventana de media altura de cuadro consultada normalmente alrededor de las barras de herramientas flotante.  
  
## Sintaxis  
  
```  
class CMiniFrameWnd : public CFrameWnd  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::CMiniFrameWnd](../Topic/CMiniFrameWnd::CMiniFrameWnd.md)|Crea un objeto `CMiniFrameWnd`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMiniFrameWnd::Create](../Topic/CMiniFrameWnd::Create.md)|crea un objeto de `CMiniFrameWnd` después de la construcción.|  
|[CMiniFrameWnd::CreateEx](../Topic/CMiniFrameWnd::CreateEx.md)|crea un objeto de `CMiniFrameWnd` \(con opciones adicionales\) después de la construcción.|  
  
## Comentarios  
 Estas ventanas de marco recudido se comportan como ventanas normales de cuadro, salvo que no tienen minimizar\/maximizan botones o menús y tiene que hacer clic en el menú sistema despedirlos únicamente.  
  
 Para utilizar un objeto de `CMiniFrameWnd` , primero define el objeto.  Llamar a continuación a la función miembro de [Crear](../Topic/CMiniFrameWnd::Create.md) para mostrar la ventana de marco recudido.  
  
 Para obtener más información sobre cómo utilizar los objetos de `CMiniFrameWnd` , vea el artículo [Acoplamiento y barras de herramientas flotante](../../mfc/docking-and-floating-toolbars.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CFrameWnd](../../mfc/reference/cframewnd-class.md)  
  
 `CMiniFrameWnd`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFrameWnd Class](../../mfc/reference/cframewnd-class.md)