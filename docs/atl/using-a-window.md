---
title: "Using a Window | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, ventanas"
  - "CWindow class, about CWindow class"
  - "windows [C++], ATL"
ms.assetid: b3b9cc8e-4287-486b-b080-38852bc2943a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Using a Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase [CWindow](../atl/reference/cwindow-class.md) permite utilizar una ventana.  Una vez que se asocia una ventana a un objeto de `CWindow` , puede llamar a los métodos de `CWindow` para manipular la ventana.  `CWindow` también contiene un operador de `HWND` para convertir un objeto de `CWindow` a `HWND`.  Así puede pasar un objeto de `CWindow` a cualquier función que requiere un identificador de una ventana.  Es fácil mezclar las llamadas al método de `CWindow` y las llamadas de función de Win32, sin realizar ningún objetos temporales.  
  
 Dado que `CWindow` tiene el miembro de datos sólo dos \(un identificador de ventana y las dimensiones predeterminadas\), no impone una sobrecarga en el código.  Además, muchas de la API Win32 correspondiente de ajuste de los métodos de `CWindow` funcionan simplemente.  Mediante `CWindow`, pasan al miembro de `HWND` automáticamente a la función de Win32.  
  
 Además de utilizar `CWindow` directamente, también puede derivar de para agregar datos o código a la clase.  ATL propio deriva tres clases de `CWindow`: [CWindowImpl](../atl/implementing-a-window.md), [CDialogImpl](../atl/implementing-a-dialog-box.md), y [CContainedWindowT](../atl/using-contained-windows.md).  
  
## Vea también  
 [Clases de ventanas](../atl/atl-window-classes.md)