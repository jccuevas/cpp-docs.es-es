---
title: "TOOLTIPTEXT (Estructura) | Microsoft Docs"
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
  - "TOOLTIPTEXT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "información sobre herramientas [C++], notificaciones"
  - "TOOLTIPTEXT (estructura)"
ms.assetid: 547591bf-80f5-400e-a2a7-0708cfffbb5d
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TOOLTIPTEXT (Estructura)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La escritura en [controlador de notificación de información sobre herramientas](../mfc/handling-ttn-needtext-notification-for-tool-tips.md), necesita utilizar la estructura de `TOOLTIPTEXT` .  Los miembros de la estructurade `TOOLTIPTEXT`son:  
  
 `typedef struct {`  
  
 `NMHDR     hdr;        // required for all WM_NOTIFY messages`  
  
 `LPTSTR    lpszText;   // see below`  
  
 `TCHAR     szText[80]; // buffer for tool tip text`  
  
 `HINSTANCE hinst;      // see below`  
  
 `UINT      uflags;     // flag indicating how to interpret the`  
  
 `// idFrom member of the NMHDR structure`  
  
 `// that is included in the structure`  
  
 `} TOOLTIPTEXT, FAR *LPTOOLTIPTEXT;`  
  
 `hdr`  
 Identifica la herramienta que necesita el texto.  El único miembro de esta estructura que necesite es el identificador de comando de control  El identificador de comando de control estará en el miembro de `idFrom` de la estructura de `NMHDR` , acceso con la sintaxis `hdr.idFrom`.  Vea [NMHDR](http://msdn.microsoft.com/library/windows/desktop/bb775514) para obtener una explicación de los miembros de la estructura de `NMHDR` .  
  
 `lpszText`  
 Dirección de una cadena para recibir el texto para la herramienta.  
  
 `szText`  
 Búfer que recibe el texto de información sobre herramientas.  Una aplicación puede copiar el texto de este búfer como alternativa a especificar una dirección de la cadena.  
  
 `hinst`  
 Identificador de la instancia que contiene una cadena que se utilizará como el texto de información sobre herramientas.  Si `lpszText` es la dirección del texto de información sobre herramientas, este miembro es NULL.  
  
 Cuando se procesa el mensaje de notificación de `TTN_NEEDTEXT` , especifique la cadena que se mostrará en una de las siguientes maneras:  
  
-   Copie el texto en el búfer especificado por el miembro de `szText` .  
  
-   Copie la dirección del búfer que contiene el texto al miembro de `lpszText` .  
  
-   Copie el identificador de un recurso de cadena al miembro de `lpszText` , y copie el identificador de instancia que contiene el recurso al miembro de `hinst` .  
  
## Vea también  
 [Información sobre herramientas en ventanas no derivadas de CFrameWnd](../mfc/tool-tips-in-windows-not-derived-from-cframewnd.md)