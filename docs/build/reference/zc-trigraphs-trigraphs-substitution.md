---
title: "/Zc:trigraphs (Sustituci&#243;n de tr&#237;grafos) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/Zc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/Zc (opción del compilador) (C++)"
  - "ajuste (opción del compilador)"
  - "Zc (opción del compilador) (C++)"
  - "-Zc (opción del compilador) (C++)"
ms.assetid: e3d6058f-400d-4966-a3aa-800cfdf69cbf
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /Zc:trigraphs (Sustituci&#243;n de tr&#237;grafos)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se especifica **\/Zc:trigraphs**, el compilador reemplaza una secuencia de caracteres de trígrafo utilizando un carácter de puntuación correspondiente.  Para desactivar la substitución de trígrafos, especifique **\/Zc:trigraphs\-**.  La opción **\/Zc:trigraphs** está desactivada de manera predeterminada.  
  
## Sintaxis  
  
```  
/Zc:trigraphs[-]  
```  
  
## Comentarios  
 Un trígrafo se compone de dos signos de interrogación consecutivos \("??"\) seguidos de un tercer carácter único.  Por ejemplo, el compilador reemplaza el trígrafo "??\=" por el carácter '\#'.  Use trígrafos en los archivos de origen de C que usen un juego de caracteres que no contenga representaciones gráficas adecuadas para algunos caracteres de puntuación.  
  
 Para obtener una lista de los trígrafos de C\/C\+\+ y un ejemplo que muestra cómo utilizarlos, vea [Trígrafos](../../c-language/trigraphs.md).  
  
## Vea también  
 [\/Zc \(Ajuste\)](../../build/reference/zc-conformance.md)   
 [Trígrafos](../../c-language/trigraphs.md)