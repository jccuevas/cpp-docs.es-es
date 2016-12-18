---
title: "WINDOWPLACEMENT (Estructura) | Microsoft Docs"
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
  - "WINDOWPLACEMENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "WINDOWPLACEMENT (estructura)"
ms.assetid: ea7d61f6-eb57-478e-9b08-7c1d07091aa8
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# WINDOWPLACEMENT (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `WINDOWPLACEMENT` contiene información sobre la posición de una ventana en la pantalla \#\#\#.  
  
## Sintaxis  
  
```  
  
      typedef struct tagWINDOWPLACEMENT {     /* wndpl */  
   UINT length;  
   UINT flags;  
   UINT showCmd;  
   POINT ptMinPosition;  
   POINT ptMaxPosition;  
   RECT rcNormalPosition;  
} WINDOWPLACEMENT;  
```  
  
#### Parámetros  
 *length*  
 Especifica la longitud, en bytes, de la estructura \#\#\#.  
  
 `flags`  
 Especifica marcadores que controlan la posición de la ventana minimizada y el método por la ventana es restaurada.  Este miembro puede ser uno de los siguientes indicadores:  
  
-   **WPF\_SETMINPOSITION** especifica que el x y las y\- posiciones de la ventana minimizada puede ser \#\#\#.especificado Este marcador se debe especificar si las coordenadas se establecen en el miembro de **ptMinPosition** .  
  
-   **WPF\_RESTORETOMAXIMIZED** especifica que la ventana restaurada se maximizada, independientemente de si se maximizado antes de que se minimice.  Este valor es válido sólo la próxima vez que se restaura la ventana.  No cambia el comportamiento predeterminado de la restauración.  Este marcador solamente es válido cuando el valor de **SW\_SHOWMINIMIZED** se especifica para el miembro de **showCmd** .  
  
 *showCmd*  
 Especifica el estado actual de la ventana.  Este miembro puede ser uno de los siguientes valores:  
  
-   **SW\_HIDE** oculta la ventana y pasa la activación a otra ventana.  
  
-   **SW\_MINIMIZE** Minimizes la ventana especificada y activa la ventana de nivel superior en la lista del sistema.  
  
-   **SW\_RESTORE** Activates y muestra una ventana.  Si está minimizado o se maximiza la ventana, Windows la restaura su tamaño y posición originales \(igual que **SW\_SHOWNORMAL**\).  
  
-   **SW\_SHOW** Activates una ventana y lo muestra en su tamaño y posición actual.  
  
-   **SW\_SHOWMAXIMIZED** Activates una ventana y muestra como ventana maximizada.  
  
-   **SW\_SHOWMINIMIZED** Activates una ventana y muestra como icono.  
  
-   **SW\_SHOWMINNOACTIVE** muestra una ventana como icono.  La ventana que está activa actualmente permanece activo.  
  
-   **SW\_SHOWNA** muestra una ventana en su estado actual.  La ventana que está activa actualmente permanece activo.  
  
-   **SW\_SHOWNOACTIVATE** muestra una ventana en su tamaño y posición más recientes.  La ventana que está activa actualmente permanece activo.  
  
-   **SW\_SHOWNORMAL** Activates y muestra una ventana.  Si está minimizado o se maximiza la ventana, Windows la restaura su tamaño y posición originales \(igual que **SW\_RESTORE**\).  
  
 *ptMinPosition*  
 Especifica la posición de la esquina superior izquierda de la ventana cuando se minimiza la ventana.  
  
 `ptMaxPosition`  
 Especifica la posición de la esquina superior izquierda de la ventana cuando se maximiza la ventana.  
  
 *rcNormalPosition*  
 Especifica las coordenadas de la ventana cuando la ventana está en el normal \(restaurado\) colocar.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CWnd::SetWindowPlacement](../Topic/CWnd::SetWindowPlacement.md)