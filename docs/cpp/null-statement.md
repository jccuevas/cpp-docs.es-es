---
title: "NULL (Instrucci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "expresiones [C++], null"
  - "null (instrucción)"
  - "valores nulos, expresiones"
ms.assetid: 606f5953-55f0-40c8-ae03-3ee3a819b851
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# NULL (Instrucci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La "instrucción null" es una instrucción de expresión a la que le falta la *expresión*.  Es útil cuando la sintaxis del lenguaje llama a una instrucción pero no a una evaluación de la expresión.  Consta de un punto y coma.  
  
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
  
## Vea también  
 [Expression \(Instrucción\)](../cpp/expression-statement.md)