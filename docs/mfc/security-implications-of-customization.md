---
title: "Implicaciones de seguridad de la personalizaci&#243;n | Microsoft Docs"
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
  - "MFC Feature Pack, seguridad"
  - "seguridad, MFC Feature Pack"
ms.assetid: 9be96b12-be38-43bd-a133-5d671265f7a1
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Implicaciones de seguridad de la personalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se describe una debilidad potencial de seguridad en MFC.  
  
## Punto débil potencial de seguridad  
 MFC permite al usuario personalizar la apariencia de una interfaz de usuario de la aplicación, por ejemplo, la apariencia de botones y de iconos.  MFC también admite las herramientas definido por el usuario, que permite al usuario ejecutar comandos de shell.  Una vulnerabilidad de seguridad se produce porque la configuración personalizada de la aplicación se guardan en el perfil de usuario en el registro.  Cualquiera que pueda tener acceso al registro puede editar estos valores y cambia la apariencia o el comportamiento de la aplicación.  Por ejemplo, un administrador del equipo podría suplantar a un usuario que produce la aplicación de usuario para ejecutar programas arbitrarios \(incluso desde un recurso compartido de red\).  
  
## Soluciones  
 Se recomienda cualquiera de estas tres maneras de cerrar las vulnerabilidades en el registro:  
  
-   Cifre los datos que se almacenan allí  
  
-   Almacena los datos en un archivo seguro en lugar de en el registro.  
  
     Para realizar cualquiera de estas dos primeras maneras, derive una clase de [CSettingsStore Class](../mfc/reference/csettingsstore-class.md) y reemplace los métodos para implementar el cifrado o el almacenamiento fuera del registro.  
  
-   También puede deshabilitar personalizaciones en la aplicación.  
  
## Vea también  
 [Personalización de MFC](../mfc/customization-for-mfc.md)