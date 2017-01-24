---
title: "CWinApp y el Asistente para aplicaciones MFC | Microsoft Docs"
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
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "asistentes para aplicaciones [C++], y CWinApp"
  - "CWinApp (clase), y Asistente para aplicaciones MFC"
  - "MFC [C++], controles wizard"
ms.assetid: f8ac0491-3302-4e46-981d-0790624eb8a2
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CWinApp y el Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando crea una aplicación esqueleto, el asistente para aplicaciones MFC declara una clase de aplicación derivada de [CWinApp](../mfc/reference/cwinapp-class.md).  El asistente para aplicaciones MFC también genera un archivo de implementación que contiene los elementos siguientes:  
  
-   Un mapa de mensajes para la clase de aplicación.  
  
-   Un constructor de clase vacío.  
  
-   Una variable que declara el único objeto de clase.  
  
-   Una implementación estándar de funciones miembro de `InitInstance` .  
  
 La clase de aplicación se coloca en los archivos de encabezado y de main del proyecto.  Los nombres de clase y de los archivos creados se basan en el nombre de proyecto que se proporciona en el asistente para aplicaciones MFC.  La manera más fácil de ver el código de estas clases se con [vista de clases](http://msdn.microsoft.com/es-es/8d7430a9-3e33-454c-a9e1-a85e3d2db925).  
  
 Las implementaciones y el mapa estándar de mensaje proporcionado son adecuados para muchos propósitos, pero puede modificarlos según sea necesario.  El más interesante de estas implementaciones es la función miembro de `InitInstance` .  Normalmente, agregará código a la implementación básica de `InitInstance`.  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)   
 [Funciones miembro de CWinApp que se pueden sobrecargar](../mfc/overridable-cwinapp-member-functions.md)   
 [Servicios especiales de CWinApp](../mfc/special-cwinapp-services.md)