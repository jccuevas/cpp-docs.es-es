---
title: "Traducci&#243;n: Diagn&#243;stico | Microsoft Docs"
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
ms.assetid: 3730ca7c-0147-452d-bd4a-6a1e97e9793e
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Traducci&#243;n: Diagn&#243;stico
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 2.1.1.3** Cómo se identifica un diagnóstico  
  
 Microsoft C muestra mensajes de error con el formato:  
  
```  
  
filename( line-number ) : diagnostic Cnumber message  
```  
  
 donde *filename* es el nombre del archivo de código fuente en el que se encontró el error; *line\-number* es el número de línea en el que el compilador detectó el error; `diagnostic` es un error o advertencia; `number` es un número único de cuatro dígitos \(precedido de una **C**, como se indica en la sintaxis\) que identifica el error o advertencia; `message` es un mensaje explicativo.  
  
## Vea también  
 [Comportamiento definido por la implementación](../c-language/implementation-defined-behavior.md)