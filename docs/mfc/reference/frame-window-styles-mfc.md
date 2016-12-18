---
title: "Estilos de ventana de marco (MFC) | Microsoft Docs"
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
  - "FWS_ADDTOTITLE"
  - "FWS_SNAPTOBARS"
  - "FWS_PREFIXTITLE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ventanas de marco, estilos"
  - "FWS_ADDTOTITLE (constante)"
  - "FWS_PREFIXTITLE (constante)"
  - "FWS_SNAPTOBARS (constante)"
  - "estilos, ventanas"
ms.assetid: d21f270e-a088-4962-a2ae-8c03334b5a06
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de ventana de marco (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **FWS\_ADDTOTITLE** especifica información para anexar al final de un título de la ventana de marco.  Por ejemplo, “dibujo de Microsoft Draw en Document1”.  Puede especificar las cadenas que aparecen en la pestaña de las cadenas de plantilla de documento en el Asistente para aplicaciones.  Si necesita desactivar esta opción, reemplace la función miembro de `CWnd::PreCreateWindow` .  
  
-   **FWS\_PREFIXTITLE** muestra el nombre del documento antes del nombre de aplicación en un título de la ventana de marco.  Por ejemplo, “documento \- Wordpad”.  Puede especificar las cadenas que aparecen en la pestaña de las cadenas de plantilla de documento en el Asistente para aplicaciones.  Si necesita desactivar esta opción, reemplace la función miembro de `CWnd::PreCreateWindow` .  
  
-   Clasificación de Controles de**FWS\_SNAPTOBARS**de la ventana de marco que agrega una barra de control cuando se encuentra en una ventana flotante en lugar de acoplada a una ventana de marco.  Tamaños de este estilo la ventana para ajustarse barra de control.  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)