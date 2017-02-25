---
title: "const_cast (Operador) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "const_cast"
  - "const_cast_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "const_cast (palabra clave) [C++]"
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# const_cast (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Quita los atributos **const**, `volatile` y **\_\_unaligned** de una clase.  
  
## Sintaxis  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## Comentarios  
 Un puntero a cualquier tipo de objeto o un puntero a un miembro de datos se puede convertir explícitamente a un tipo que sea idéntico, salvo en el caso de los calificadores **const**, `volatile` y **\_\_unaligned**.  Para los punteros y las referencias, el resultado hará referencia al objeto original.  Para los punteros a miembros de datos, el resultado hará referencia al mismo miembro que el puntero original \(sin convertir\) al miembro de datos.  Según el tipo del objeto al que se hace referencia, una operación de escritura a través del puntero, referencia o puntero a miembro de datos resultante podría generar un comportamiento indefinido.  
  
 No puede utilizar el operador `const_cast` para invalidar directamente el estado constante de una variable constante.  
  
 El operador `const_cast` convierte un valor de puntero NULL al valor de puntero NULL del tipo de destino.  
  
## Ejemplo  
  
```  
// expre_const_cast_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
class CCTest {  
public:  
   void setNumber( int );  
   void printNumber() const;  
private:  
   int number;  
};  
  
void CCTest::setNumber( int num ) { number = num; }  
  
void CCTest::printNumber() const {  
   cout << "\nBefore: " << number;  
   const_cast< CCTest * >( this )->number--;  
   cout << "\nAfter: " << number;  
}  
  
int main() {  
   CCTest X;  
   X.setNumber( 8 );  
   X.printNumber();  
}  
```  
  
 En la línea que contiene `const_cast`, el tipo de datos del puntero `this` es `const CCTest *`.  El operador `const_cast` cambia el tipo de datos del puntero `this` a `CCTest *`, lo que permite que se modifique el elemento `number` miembro.  La conversión se produce únicamente para el resto de la instrucción en la que aparece.  
  
## Vea también  
 [Operadores de conversión](../cpp/casting-operators.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)