---
title: "WINDOWPOS (Estructura) | Microsoft Docs"
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
  - "WINDOWPOS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPOS (estructura)"
ms.assetid: a4ea7cd9-c4c2-4480-9c55-cbbff72195e1
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WINDOWPOS (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `WINDOWPOS` contiene información sobre el tamaño y la posición de una ventana.  
  
## Sintaxis  
  
```  
  
      typedef struct tagWINDOWPOS { /* wp */  
   HWND hwnd;  
   HWND hwndInsertAfter;  
   int x;  
   int y;  
   int cx;  
   int cy;  
   UINT flags;  
} WINDOWPOS;  
```  
  
#### Parámetros  
 *hwnd*  
 Identifica la ventana.  
  
 *hwndInsertAfter*  
 Identifica la ventana detrás de la que se coloca esta ventana.  
  
 *x*  
 Especifica la posición del borde izquierdo de la ventana.  
  
 *y*  
 Especifica la posición del borde derecho.  
  
 `cx`  
 Especifica el ancho de la ventana, en píxeles.  
  
 `cy`  
 Especifica el alto de la ventana, en píxeles.  
  
 `flags`  
 Especifica la ventana\- posición de opciones.  Este miembro puede ser uno de los siguientes valores:  
  
-   **SWP\_DRAWFRAME** dibuja un cuadro \(definido en la clase de la ventana\) alrededor de la ventana.  La ventana recibe un mensaje de `WM_NCCALCSIZE` .  
  
-   **SWP\_FRAMECHANGED** Sends un mensaje de `WM_NCCALCSIZE` a la ventana, aunque el tamaño de la ventana no se está cambiando.  Si este marcador no se especifica, se envía `WM_NCCALCSIZE` cuando se cambia el tamaño de la ventana.  
  
-   **SWP\_HIDEWINDOW** oculta la ventana.  
  
-   `SWP_NOACTIVATE` No no activar la ventana.  
  
-   **SWP\_NOCOPYBITS** descarta el contenido completo del área de cliente.  Si este marcador no se especifica, el contenido válidos del área de cliente se guardan y se copian en el área cliente después de que se haya ordenado o se coloque de nuevo la ventana.  
  
-   `SWP_NOMOVE` conserva la posición actual \(omite los miembros de **x** y de **s** \).  
  
-   Cambio de**SWP\_NOOWNERZORDER**No no la posición de la ventana propietaria en el orden Z.  
  
-   `SWP_NOSIZE` conserva el tamaño actual \(omite los miembros de **cx** y de **cy** \).  
  
-   Cambios no actualizars de**SWP\_NOREDRAW**No.  
  
-   **SWP\_NOREPOSITION** Same que **SWP\_NOOWNERZORDER**.  
  
-   **SWP\_NOSENDCHANGING** evita que la ventana reciba el mensaje de `WM_WINDOWPOSCHANGING` .  
  
-   `SWP_NOZORDER` conserva el orden de la actual \(omite el miembro de **hwndInsertAfter** \).  
  
-   **SWP\_SHOWWINDOW** muestra la ventana.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::OnWindowPosChanging](../Topic/CWnd::OnWindowPosChanging.md)