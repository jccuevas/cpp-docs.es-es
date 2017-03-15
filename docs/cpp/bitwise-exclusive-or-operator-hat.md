---
title: "Operador OR exclusivo bit a bit: ^ | Microsoft Docs"
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
  - "^ (operador)"
  - "operadores bit a bit, OR (operador)"
  - "OR exclusivo (operador)"
  - "operadores [C++], bit a bit"
  - "operadores [C++], lógico"
  - "OR (operador), exclusivo bit a bit"
  - "XOR (operador)"
ms.assetid: f9185d85-65d5-4f64-a6d6-679758d52217
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador OR exclusivo bit a bit: ^
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
expression ^ expression  
```  
  
## Comentarios  
 El operador OR exclusivo bit a bit \(**^**\) compara cada bit de su primer operando con el bit correspondiente de su segundo operando.  Si un bit es 0 y el otro bit es 1, el bit del resultado correspondiente se establece en 1.  De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos del operador OR exclusivo bit a bit deben ser de tipos enteros.  Las conversiones aritméticas habituales descritas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos.  
  
## Palabra clave de operador para ^  
 El operador **xor** es el equivalente de texto de **^**.  Hay dos maneras de tener acceso al operador **xor** en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción del compilador [\/Za](../build/reference/za-ze-disable-language-extensions.md) \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Bitwise_Exclusive_OR_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise exclusive OR  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0x5555;      // pattern 0101 ...  
   unsigned short b = 0xFFFF;      // pattern 1111 ...  
  
   cout  << hex << ( a ^ b ) << endl;   // prints "aaaa" pattern 1010 ...  
}  
```  
  
## Vea también  
 [Operadores bit a bit de C\+\+](../misc/cpp-bitwise-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)