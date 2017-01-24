---
title: "Operador OR inclusivo bit a bit: | | Microsoft Docs"
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
  - "bitor"
  - "|"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "| (operador)"
  - "operadores bit a bit, OR (operador)"
  - "OR inclusivo (operador)"
  - "OR (operador), inclusivo bit a bit"
ms.assetid: 4c8a6a68-d828-447d-875a-aedb4ce3aa9a
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador OR inclusivo bit a bit: |
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
expression   
|  
 expression  
  
```  
  
## Comentarios  
 El operador OR inclusivo bit a bit \(         **&#124;** \) compara cada bit del primer operando con el bit correspondiente del segundo operando.  Si uno de los dos bits es 1, el bit del resultado correspondiente se establece en 1.  De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos del operador OR inclusivo bit a bit deben ser de tipos enteros.  Las conversiones aritméticas habituales descritas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos.  
  
## Palabra clave del operador para &#124;  
 El operador `bitor` es el equivalente de texto de              **&#124;** .  Hay dos maneras de obtener acceso al operador `bitor` en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Bitwise_Inclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise inclusive OR  
#include <iostream>  
using namespace std;  
  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a | b ) << endl;   // prints "ffff" pattern 1111 ...  
}  
```  
  
## Vea también  
 [Operadores bit a bit de C\+\+](../misc/cpp-bitwise-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)