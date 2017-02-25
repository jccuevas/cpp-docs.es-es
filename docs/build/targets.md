---
title: "Destinos | Microsoft Docs"
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
  - "destinos, especificar en NMAKE"
ms.assetid: 826ee849-4278-4c6e-97c3-79a2b5fe6463
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Destinos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En una línea de dependencia, se pueden especificar uno o varios destinos usando cualquier nombre de archivo, nombre de directorio o [pseudodestino](../build/pseudotargets.md) válido.  Si hay varios destinos, se han de separar con uno o más espacios o tabulaciones.  Los destinos no distinguen entre mayúsculas y minúsculas.  Se permiten rutas de acceso con nombres de archivos.  Un destino no puede superar los 256 caracteres.  Si el destino que precede al signo de dos puntos está formado por un solo carácter, se ha de utilizar un espacio de separación; de lo contrario, NMAKE interpreta la combinación de letra y dos puntos como un especificador de unidad.  
  
## ¿Sobre qué desea obtener más información?  
 [Pseudodestinos](../build/pseudotargets.md)  
  
 [Destinos múltiples](../build/multiple-targets.md)  
  
 [Dependencias acumuladas](../build/cumulative-dependencies.md)  
  
 [Destinos de bloques de descripción múltiples](../build/targets-in-multiple-description-blocks.md)  
  
 [Efectos secundarios de las relaciones de dependencia](../build/dependency-side-effects.md)  
  
## Vea también  
 [Bloques de descripción](../build/description-blocks.md)