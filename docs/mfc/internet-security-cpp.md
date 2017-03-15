---
title: "Seguridad de Internet (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "seguridad de acceso del código [C++], consideraciones de seguridad de Internet"
  - "firma de código [C++]"
  - "firma de código [C++], seguridad de Internet"
  - "firmas digitales, seguridad de Internet"
  - "aplicaciones de Internet, seguridad"
  - "recintos"
  - "seguridad [MFC]"
  - "seguridad [MFC], Internet"
  - "seguridad de aplicaciones web"
  - "seguridad de aplicaciones web, enfoques de seguridad de Internet"
ms.assetid: bf0da697-81bc-41f0-83fa-d7f82ed83df8
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Seguridad de Internet (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La seguridad del código es un problema importante para los desarrolladores y para los usuarios de las aplicaciones de internet.  Hay riesgos: el código malintencionado, el código que se ha tratado de manipulación, y el código de sitios desconocidos o crea.  
  
 Existen dos métodos básicos a la seguridad al desarrollar para internet.  El primer se denomina “espacio aislado”. En este enfoque, una aplicación se limita a un conjunto determinado de API, y se excluye los potencialmente peligrosos como E\/S de archivo donde un programa podría destruir datos en un equipo del usuario.  El segundo se implementa utilizando firmas digitales.  Se conoce este enfoque como “shrinkwrap” para internet.  El código se comprueba y se firma utilizando la tecnología de clave privada y clave pública.  Antes de ejecutar el código, la firma digital se comprueba para asegurarse de que el código sea de un origen autenticado conocido, y que el código no se ha modificado desde que se ha firmado.  
  
 En el primer caso, se confirma que la aplicación no realizará ningún daño y confía en el origen de la aplicación.  En el segundo, las firmas digitales se utilizan para comprobar la autenticidad.  La firma digital es un estándar de la industria usado para identificar y proporcionar los detalles sobre el editor de código.  La tecnología se basa en los estándares, incluidos RSA y X.509.  Los exploradores suelen permitir a los usuarios elegir si desea descargar y ejecutar código de origen desconocido.  
  
 Información adicional sobre la firma de código y otras medidas de seguridad está disponible en Web.  La información se puede obtener acceso a través del sitio web de MSDN Online Workshop en [http:\/\/msdn.microsoft.com\/](http://msdn.microsoft.com/), o a través del World Wide Web Consortium en [http:\/\/www.w3.org\/](http://www.w3.org/).  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)