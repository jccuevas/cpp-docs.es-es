---
title: "Personalizaci&#243;n de MFC | Microsoft Docs"
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
  - "personalizaciones, extensiones MFC"
ms.assetid: 3b1b7532-8cc9-48dc-9bbe-7fd4060530b5
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 17
---
# Personalizaci&#243;n de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema proporciona sugerencias para personalizar una aplicación MFC.  
  
## Personalizaciones generales  
 Puede guardar y cargar el estado de aplicación al registro.  Cuando se habilita esta opción, la aplicación cargará su estado inicial del registro.  Si cambia el diseño inicial de acoplamiento para la aplicación, tendrá que borrar los datos del Registro de la aplicación.  Si no, los datos del registro reemplazará cualquier cambio realizado en el diseño inicial.  
  
## Personalizaciones Clase\-específicas  
 Las sugerencias adicionales de personalización se encuentran en los temas siguientes:  
  
-   [CBasePane Class](../mfc/reference/cbasepane-class.md)  
  
-   [CDockablePane Class](../mfc/reference/cdockablepane-class.md)  
  
-   [CDockingManager Class](../mfc/reference/cdockingmanager-class.md)  
  
-   [CMFCBaseTabCtrl Class](../mfc/reference/cmfcbasetabctrl-class.md)  
  
## Sugerencias adicionales de personalización  
 [Personalización del teclado y del mouse](../mfc/keyboard-and-mouse-customization.md)  
  
 [Herramientas definidas por el usuario](../mfc/user-defined-tools.md)  
  
## Vea también  
 [Aplicaciones de escritorio de MFC](../mfc/mfc-desktop-applications.md)   
 [Implicaciones de seguridad de la personalización](../mfc/security-implications-of-customization.md)