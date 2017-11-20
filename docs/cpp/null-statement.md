---
title: "NULL instrucción | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- expressions [C++], null
- null statement
- null values, expressions
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ecaa8d968efa9a3cd8c700d3d4dfe4cae0f0dd53
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="null-statement"></a>NULL (Instrucción)
La "instrucción null" es una instrucción de expresión con el *expresión* falta. Es útil cuando la sintaxis del lenguaje llama a una instrucción pero no a una evaluación de la expresión. Consta de un punto y coma.  
  
 Las instrucciones null se utilizan normalmente como marcadores de posición en instrucciones de iteración o como instrucciones en las que se colocan etiquetas al final de las instrucciones compuestas o funciones.  
  
 El siguiente fragmento de código muestra cómo copiar una cadena a otra e incorpora la instrucción null:  
  
```  
// null_statement.cpp  
char *myStrCpy( char *Dest, const char *Source )  
{  
    char *DestStart = Dest;  
  
    // Assign value pointed to by Source to  
    // Dest until the end-of-string 0 is  
    // encountered.  
    while( *Dest++ = *Source++ )  
        ;   // Null statement.  
  
    return DestStart;  
}  
  
int main()  
{  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expression (Instrucción)](../cpp/expression-statement.md)