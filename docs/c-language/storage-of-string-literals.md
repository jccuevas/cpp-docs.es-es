---
title: "Almacenamiento de literales de cadena | Microsoft Docs"
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
  - "literales de cadena, almacenamiento"
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Almacenamiento de literales de cadena
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los caracteres de una cadena literal se almacenan en orden en ubicaciones de memoria contiguas.  Una secuencia de escape \(tal como **\\\\** o **\\"**\) dentro de un literal de cadena cuenta como un carácter individual.  Un carácter null \(representado por la secuencia de escape **\\0**\) se anexa automáticamente y marca el final de cada literal de cadena. \(Esto ocurre durante la [fase de traslación](../preprocessor/phases-of-translation.md) 7.\) Tenga en cuenta que el compilador no puede almacenar dos cadenas idénticas en dos direcciones distintas.  [\/GF](../build/reference/gf-eliminate-duplicate-strings.md) fuerza al compilador a colocar una única copia de cadenas idénticas en el archivo ejecutable.  
  
## Comentarios  
 **Específicos de Microsoft**  
  
 Las cadenas tienen duración de almacenamiento estático.  Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener información sobre la duración del almacenamiento.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)