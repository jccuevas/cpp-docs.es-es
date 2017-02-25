---
title: "Error PRJ0025 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0025"
ms.assetid: 57725c78-bc63-44f3-9667-2969b2d7c41d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error PRJ0025 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El archivo por lotes 'archivo' incluye contenido Unicode que no se puede traducir a la página de códigos ANSI del usuario.  
  
 ***Contenido UNICODE del archivo***  
  
 El sistema de proyectos encontró contenido Unicode en una regla de compilación personalizada o un evento de compilación que no se puede traducir correctamente a la página de códigos ANSI actual del sistema instalado en el equipo del usuario.  
  
 La solución de este error es actualizar el contenido de la regla de compilación o el evento de compilación para que utilice ANSI o instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.  
  
 Para obtener más información acerca de los pasos de generación personalizada y los eventos de compilación, vea [Introducción a los pasos de generación personalizada y los eventos de compilación](../../ide/understanding-custom-build-steps-and-build-events.md).