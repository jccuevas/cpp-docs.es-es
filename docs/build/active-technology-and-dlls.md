---
title: "Tecnolog&#237;a activa y archivos DLL | Microsoft Docs"
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
  - "tecnología activa [C++]"
  - "automatización [C++], DLL"
  - "DLL [C++], tecnología activa"
  - "DLL de servidor en proceso"
  - "DLL de MFC [C++], tecnología activa"
ms.assetid: 3ed27f8d-164a-4562-ad61-9f2333404cc7
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Tecnolog&#237;a activa y archivos DLL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tecnología activa permite a los servidores de objetos implementarse completamente dentro de un archivo DLL.  Este tipo de servidor se denomina servidor en proceso.  MFC no ofrece una compatibilidad total con los servidores en proceso con respecto a todas las características de edición visual, fundamentalmente porque la tecnología activa no proporciona una forma de que un servidor se enlace con el bucle principal de mensajes del contenedor.  MFC requiere acceso al bucle de mensajes de la aplicación contenedora para controlar las teclas de aceleración y realizar el procesamiento de los tiempos de inactividad.  
  
 Si está programando un servidor de automatización y este servidor no tiene interfaz de usuario, puede convertir el servidor en un servidor en proceso y colocarlo dentro de un archivo DLL.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Servidores de automatización](../mfc/automation-servers.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)