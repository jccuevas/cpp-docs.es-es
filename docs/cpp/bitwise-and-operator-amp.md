---
title: "Operador AND bit a bit: &amp; | Microsoft Docs"
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
  - "bitand"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& (operador), operadores bit a bit"
  - "AND (operador)"
  - "operadores bit a bit, AND (operador)"
ms.assetid: 76f40de3-c417-47b9-8a77-532f3fc990a5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador AND bit a bit: &amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
expression   
&  
 expression  
  
```  
  
## Comentarios  
 Las expresiones pueden ser otras expresiones de tipo and, o \(en función de las restricciones de tipo que se mencionan más abajo\), expresiones de igualdad, expresiones relacionales, expresiones aditivas, expresiones multiplicativas, expresiones de puntero a miembro, expresiones de conversión, expresiones unarias, expresiones de postfijo o expresiones primarias.  
  
 El operador AND bit a bit \(**&**\) compara cada bit del primer operando con el bit correspondiente del segundo operando.  Si ambos bits son 1, el bit del resultado correspondiente se establece en 1.  De lo contrario, el bit del resultado correspondiente se establece en 0.  
  
 Ambos operandos para el operador AND bit a bit deben ser de tipos enteros.  Las conversiones aritméticas habituales descritas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos.  
  
## Palabra clave del operador para &  
 El operador `bitand` es el equivalente de texto de **&**.  Hay dos maneras de obtener acceso al operador `bitand` en los programas: incluir el archivo de encabezado `iso646.h` o compilar con la opción [\/Za](../build/reference/za-ze-disable-language-extensions.md) del compilador \(deshabilitar extensiones de lenguaje\).  
  
## Ejemplo  
  
```  
// expre_Bitwise_AND_Operator.cpp  
// compile with: /EHsc  
// Demonstrate bitwise AND  
#include <iostream>  
using namespace std;  
int main() {  
   unsigned short a = 0xFFFF;      // pattern 1111 ...  
   unsigned short b = 0xAAAA;      // pattern 1010 ...  
  
   cout  << hex << ( a & b ) << endl;   // prints "aaaa", pattern 1010 ...  
}  
```  
  
## Vea también  
 [Operadores bit a bit de C\+\+](../misc/cpp-bitwise-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores bit a bit de C](../c-language/c-bitwise-operators.md)