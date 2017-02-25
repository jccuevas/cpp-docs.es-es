---
title: "Operadores de preprocesador | Microsoft Docs"
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
  - "operadores [C++], preprocesador"
  - "operadores de preprocesador"
ms.assetid: 884126d1-0ce2-48b6-9e06-8a2d7c4a9656
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Operadores de preprocesador
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se utilizan cuatro operadores específicos del preprocesador en el contexto de la directiva `#define` \(vea la lista siguiente para obtener un resumen de cada uno de ellos\).  En las próximas tres secciones se explican los operadores de generación de cadenas, generación de caracteres y pegado de token.  Para obtener información sobre el operador **defined**, vea [Directivas \#if, \#elif, \#else y \#endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md).  
  
|Operador|Acción|  
|--------------|------------|  
|[Operador de generación de cadenas \(\#\)](../preprocessor/stringizing-operator-hash.md)|Hace que el argumento real correspondiente se delimite con comillas dobles|  
|[Operador de generación de caracteres \(\#@\)](../preprocessor/charizing-operator-hash-at.md)|Hace que el argumento correspondiente se delimite con comillas simples y se trate como un carácter \(Específicos de Microsoft\)|  
|[Operador de pegado de token \(\#\#\)](../preprocessor/token-pasting-operator-hash-hash.md)|Permite concatenar tokens utilizados como argumentos reales para formar otros tokens|  
|[Operador defined](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md)|Simplifica la escritura de expresiones compuestas en determinadas directivas de macro|  
  
## Vea también  
 [Directivas de preprocesador](../preprocessor/preprocessor-directives.md)   
 [Macros predefinidas](../preprocessor/predefined-macros.md)   
 [Referencia del preprocesador de C\/C\+\+](../preprocessor/c-cpp-preprocessor-reference.md)