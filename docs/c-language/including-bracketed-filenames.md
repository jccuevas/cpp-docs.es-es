---
title: "Incluir nombres de archivo entre corchetes | Microsoft Docs"
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
  - "C"
ms.assetid: 6a4e5411-c35e-48b8-90ef-b37ac324ed94
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Incluir nombres de archivo entre corchetes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.8.2** El método para buscar archivos de código fuente que se pueden incluir  
  
 Para las especificaciones de archivo incluidas entre corchetes angulares, el preprocesador no busca en los directorios de los archivos principales.  Un archivo "principal" es el archivo que contiene la directiva [\#include](../preprocessor/hash-include-directive-c-cpp.md).  En su lugar, comienza buscando el archivo en los directorios especificados en la línea de comandos del compilador detrás de \/I.  Si la opción \/I no está presente o produce un error, el preprocesador utiliza la variable de entorno INCLUDE para buscar cualquier archivo de inclusión dentro de los paréntesis angulares.  La variable de entorno INCLUDE puede contener varias rutas de acceso, separadas por punto y coma \(**;**\).  Si aparece más de un directorio como parte de la opción \/I o en la variable de entorno INCLUDE, el preprocesador los busca en el orden en que aparecen.  
  
## Vea también  
 [Preprocesar directivas](../c-language/preprocessing-directives.md)