---
title: "Error PRJ0024 al compilar el proyecto | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0024"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0024"
ms.assetid: 8bde6368-6c1b-4e04-bc5e-3c6d0b8fa1d7
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0024 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La ruta de acceso de Unicode 'ruta' no se puede traducir a la página de códigos ANSI del usuario.  
  
 ***ruta de acceso***  es la versión Unicode original de la cadena de ruta.  Este error puede producirse cuando hay una ruta Unicode que no se puede traducir directamente a ANSI para la página de códigos actual del sistema.  
  
 Este error puede producirse cuando trabaje con un proyecto desarrollado en un sistema que utiliza una página de códigos que falta en el sistema de su equipo.  
  
 La solución de este error es actualizar la ruta para utilizar texto ANSI o instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.