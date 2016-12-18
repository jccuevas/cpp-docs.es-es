---
title: "Error PRJ0035 al compilar el proyecto | Microsoft Docs"
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
  - "PRJ0035"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0035"
ms.assetid: 0667116d-338c-40a4-972c-da875f778cb5
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error PRJ0035 al compilar el proyecto
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El archivo XML 'archivo' incluye contenido Unicode que no se puede traducir a la página de códigos ANSI del usuario.  
  
 ***Contenido UNICODE del archivo***  
  
 ***archivo***  es el archivo XML creado como línea de comandos para la herramienta de implementación web.  
  
 El sistema de proyectos encontró caracteres Unicode en algunas propiedades de la página de propiedades Implementación Web, que no pueden traducirse adecuadamente a ANSI.  
  
 La solución para este error es actualizar el contenido de la propiedad para que utilice ANSI o instalar la página de códigos en el equipo y establecerla como la predeterminada del sistema.