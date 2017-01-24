---
title: "Estilos de ventana | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WS_MINIMIZEBOX"
  - "WS_SIZEBOX"
  - "WS_CLIPCHILDREN"
  - "WS_TILED"
  - "WS_GROUP"
  - "WS_VSCROLL"
  - "WS_CHILD"
  - "WS_TABSTOP"
  - "WS_HSCROLL"
  - "WS_THICKFRAME"
  - "WS_DISABLED"
  - "WS_POPUP"
  - "WS_ICONIC"
  - "WS_MAXIMIZE"
  - "WS_VISIBLE"
  - "WS_POPUPWINDOW"
  - "WS_TILEDWINDOW"
  - "WS_DLGFRAME"
  - "WS_MINIMIZE"
  - "WS_CAPTION"
  - "WS_OVERLAPPED"
  - "WS_BORDER"
  - "WS_MAXIMIZEBOX"
  - "WS_OVERLAPPEDWINDOW"
  - "WS_SYSMENU"
  - "WS_CHILDWINDOW"
  - "WS_CLIPSIBLINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estilos, ventanas"
  - "estilos de ventanas"
  - "estilos de ventanas, en MFC"
  - "WS_BORDER (constante)"
  - "WS_CAPTION (constante)"
  - "WS_CHILD (constante)"
  - "WS_CHILDWINDOW (constante)"
  - "WS_CLIPCHILDREN (constante)"
  - "WS_CLIPSIBLINGS (constante)"
  - "WS_DISABLED (constante)"
  - "WS_DLGFRAME (constante)"
  - "WS_GROUP (constante)"
  - "WS_HSCROLL (constante)"
  - "WS_ICONIC (constante)"
  - "WS_MAXIMIZE (constante)"
  - "WS_MAXIMIZEBOX (constante)"
  - "WS_MINIMIZE (constante)"
  - "WS_MINIMIZEBOX (constante)"
  - "WS_OVERLAPPED (constante)"
  - "WS_OVERLAPPEDWINDOW (constante)"
  - "WS_POPUP (constante)"
  - "WS_POPUPWINDOW (constante)"
  - "WS_SIZEBOX (constante)"
  - "WS_SYSMENU (constante)"
  - "WS_TABSTOP (constante)"
  - "WS_THICKFRAME (constante)"
  - "WS_TILED (constante)"
  - "WS_TILEDWINDOW (constante)"
  - "WS_VISIBLE (constante)"
  - "WS_VSCROLL (constante)"
ms.assetid: c85ffbe4-f4ff-4227-917a-48ec4a411842
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de ventana
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   `WS_BORDER` Crea una ventana con un borde.  
  
-   **WS\_CAPTION** crea una ventana que tiene una barra de título \(implica el estilo `WS_BORDER`\).  No se puede utilizar con el estilo **WS\_DLGFRAME**.  
  
-   **WS\_CHILD** crea una ventana secundaria.  No se puede usar con el estilo `WS_POPUP`.  
  
-   **WS\_CHILDWINDOW** igual que el estilo **WS\_CHILD**.  
  
-   **WS\_CLIPCHILDREN** excluye el área ocupada por las ventanas secundarias cuando se dibuja dentro de la ventana primaria.  Se utiliza al crear la ventana primaria.  
  
-   **WS\_CLIPSIBLINGS** recorta las ventanas secundarias en relación con las demás; es decir, cuando una ventana secundaria determinada recibe un mensaje del dibujo, el estilo **WS\_CLIPSIBLINGS** recorta todas las demás ventanas secundarias superpuestas fuera de la región de la ventana secundaria que se actualiza. \(Si **WS\_CLIPSIBLINGS** no se especifica y las ventanas secundarias se superponen, cuando se dibuja en el área de cliente de una ventana secundaria, es posible dibujar dentro del área cliente de una ventana secundaria vecina.\) Para el uso solo con el estilo **WS\_CHILD**.  
  
-   **WS\_DISABLED** crea una ventana que está deshabilitada inicialmente.  
  
-   **WS\_DLGFRAME** crea una ventana con un borde doble pero ningún título.  
  
-   **WS\_GROUP** especifica el primer control de un grupo de controles en los que el usuario puede desplazarse desde un control al siguiente con las teclas de dirección.  Todos los controles definidos con el estilo **FALSE** de **WS\_GROUP** después del primer control pertenecen al mismo grupo.  El control siguiente con el estilo **WS\_GROUP** inicia el grupo siguiente \(es decir, un grupo termina donde comienza el siguiente\).  
  
-   **WS\_HSCROLL** crea una ventana que tiene una barra de desplazamiento horizontal.  
  
-   **WS\_ICONIC** crea una ventana que se minimiza inicialmente.  Igual que el estilo de **WS\_MINIMIZE**.  
  
-   **WS\_MAXIMIZE** crea una ventana de tamaño máximo.  
  
-   **WS\_MAXIMIZEBOX** crea una ventana con un botón para maximizar.  
  
-   **WS\_MINIMIZE** crea una ventana que se minimiza inicialmente.  Para el uso solo con el estilo **WS\_OVERLAPPED**.  
  
-   **WS\_MINIMIZEBOX** crea una ventana con un botón para minimizar.  
  
-   **WS\_OVERLAPPED** crea una ventana superpuesta.  Una ventana superpuesta tiene normalmente una leyenda y un borde.  
  
-   **WS\_OVERLAPPEDWINDOW** crea una ventana superpuesta con los estilos **WS\_OVERLAPPED**, **WS\_CAPTION**, **WS\_SYSMENU**, **WS\_THICKFRAME**, **WS\_MINIMIZEBOX** y **WS\_MAXIMIZEBOX**.  
  
-   `WS_POPUP` Abre una ventana emergente.  No se puede utilizar con el estilo **WS\_CHILD**.  
  
-   **WS\_POPUPWINDOW** crea una ventana emergente con los estilos `WS_BORDER`, `WS_POPUP` y **WS\_SYSMENU**.  El estilo **WS\_CAPTION** se debe combinar con el estilo **WS\_POPUPWINDOW** para crear el menú de control visible.  
  
-   **WS\_SIZEBOX** Crea una ventana con un borde de tamaño ajustable.  Igual que el estilo de **WS\_THICKFRAME**.  
  
-   **WS\_SYSMENU** Crea una ventana que tiene un cuadro del menú Control en su barra de título  Sólo se utiliza en ventanas con las barras de título.  
  
-   **WS\_TABSTOP** especifica uno de cualquier número de controles en los que el usuario pueda desplazarse mediante la tecla TAB.  La tecla TAB desplaza al usuario al control siguiente especificado por el estilo **WS\_TABSTOP**.  
  
-   **WS\_THICKFRAME** Crea una ventana con un marco grueso que pueda usarse para cambiar el tamaño de la ventana  
  
-   **WS\_TILED** crea una ventana superpuesta.  Una ventana superpuesta tiene una barra de título y un borde.  Igual que el estilo de **WS\_OVERLAPPED** .  
  
-   **WS\_TILEDWINDOW** crea una ventana superpuesta con los estilos **WS\_OVERLAPPED**, **WS\_CAPTION**, **WS\_SYSMENU**, **WS\_THICKFRAME**, **WS\_MINIMIZEBOX** y **WS\_MAXIMIZEBOX**.  Igual que el estilo de **WS\_OVERLAPPEDWINDOW**.  
  
-   **WS\_VISIBLE** crea una ventana que se muestra inicialmente.  
  
-   **WS\_VSCROLL** crea una ventana que tiene una barra de desplazamiento vertical.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CWnd::Create](../Topic/CWnd::Create.md)   
 [CWnd::CreateEx](../Topic/CWnd::CreateEx.md)   
 [CreateWindow](http://msdn.microsoft.com/library/windows/desktop/ms632679)