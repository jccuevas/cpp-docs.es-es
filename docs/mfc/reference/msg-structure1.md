---
title: "Estructura de mensaje-1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "estructura MSG"
ms.assetid: dc166d27-9423-41f1-9599-5ba76d2f0138
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# MSG (Estructura)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La estructura de `MSG` contiene información de mensaje de la cola de subproceso.  
  
## Sintaxis  
  
```  
  
      typedef struct tagMSG {     // msg    
   HWND hwnd;  
   UINT message;  
   WPARAM wParam;  
   LPARAM lParam;  
   DWORD time;  
   POINT pt;  
} MSG;  
```  
  
#### Parámetros  
 *hwnd*  
 Identifica la ventana cuyo procedimiento de ventana recibe el mensaje.  
  
 `message`  
 Especifica el número de mensaje.  
  
 `wParam`  
 Especifica información adicional sobre el mensaje.  El significado exacto depende del valor del miembro de **mensaje** .  
  
 `lParam`  
 Especifica información adicional sobre el mensaje.  El significado exacto depende del valor del miembro de **mensaje** .  
  
 `time`  
 Especifica el tiempo en el que se envió el mensaje.  
  
 `pt`  
 Especifica la posición del cursor, en coordenadas de la pantalla, cuando el mensaje se envió.  
  
## Requisitos  
 **Header:** winuser.h  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)