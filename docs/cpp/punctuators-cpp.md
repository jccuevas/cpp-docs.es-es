---
title: "Signos de puntuaci&#243;n de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - ";"
  - ","
  - "{"
  - "}"
  - "("
  - ")"
  - "["
  - "]"
  - "!"
  - "%"
  - "^"
  - "*"
  - """
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "signos de puntuación"
ms.assetid: 1521564c-a977-488a-9490-068079897592
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Signos de puntuaci&#243;n de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los signos de puntuación en C\+\+ tienen un significado sintáctico y semántico para el compilador, pero, por sí mismos, no especifican una operación que produzca un valor.  Algunos signos de puntuación, solos o combinados, también pueden ser operadores de C\+\+ o ser significativos para el preprocesador.  
  
 Cualquiera de los siguientes caracteres se consideran signos de puntuación:  
  
```  
! % ^ & * ( ) – + = { } | ~  
[ ] \ ; ' : " < > ? , . / #  
```  
  
 Los signos de puntuación **\[ \]**, **\( \)** y **{ }** deben aparecer en parejas después de la [fase de traducción](../preprocessor/phases-of-translation.md) 4.  
  
## Vea también  
 [Convenciones léxicas](../cpp/lexical-conventions.md)