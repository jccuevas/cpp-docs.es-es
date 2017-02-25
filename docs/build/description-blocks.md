---
title: "Bloques de descripci&#243;n | Microsoft Docs"
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
  - "bloques, description"
  - "bloques de descripción"
  - "NMAKE (programa), bloques de descripción"
ms.assetid: 1321f228-d389-40ac-b0cd-4f6e9293602b
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Bloques de descripci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un bloque de descripción es una línea de dependencia seguida opcionalmente de un bloque de comandos:  
  
```  
targets... : dependents...  
    commands...  
```  
  
 Una línea de dependencia especifica uno o varios destinos y ninguno o varios dependientes.  Un destino debe estar situado al principio de la línea.  Los destinos se separan de los dependientes mediante un signo de dos puntos \(:\); se permiten espacios o tabulaciones.  Para dividir la línea, se ha de utilizar una barra inversa \(\\\) después de un destino o un dependiente.  Si un destino no existe, tiene una marca de tiempo anterior a un dependiente, o es un [pseudodestino](../build/pseudotargets.md), NMAKE ejecuta los comandos.  Si un dependiente es un destino en cualquier otra parte y no existe o no está actualizado con respecto a sus propios dependientes, NMAKE lo actualiza antes de actualizar la dependencia actual.  
  
## ¿Sobre qué desea obtener más información?  
 [Destinos](../build/targets.md)  
  
 [Dependientes](../build/dependents.md)  
  
## Vea también  
 [Referencia de NMAKE](../build/nmake-reference.md)