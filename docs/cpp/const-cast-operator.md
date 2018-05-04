---
title: const_cast (operador) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- const_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ed5daf503024b2c3f843faeeaedbd9ec9bf64b7c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="constcast-operator"></a>const_cast (Operador)
Quita el **const**, `volatile`, y **__unaligned** atributos de una clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
const_cast <   
type-id  
 > (   
expression  
 )  
  
```  
  
## <a name="remarks"></a>Comentarios  
 Un puntero a cualquier tipo de objeto o un puntero a un miembro de datos se puede convertir explícitamente a un tipo que es idéntico, salvo por la **const**, `volatile`, y **__unaligned** calificadores. Para los punteros y las referencias, el resultado hará referencia al objeto original. Para los punteros a miembros de datos, el resultado hará referencia al mismo miembro que el puntero original (sin convertir) al miembro de datos. Según el tipo del objeto al que se hace referencia, una operación de escritura a través del puntero, referencia o puntero a miembro de datos resultante podría generar un comportamiento indefinido.  
  
 No puede utilizar el operador `const_cast` para invalidar directamente el estado constante de una variable constante.  
  
 El operador `const_cast` convierte un valor de puntero NULL al valor de puntero NULL del tipo de destino.  
  
## <a name="example"></a>Ejemplo  
  
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
  
 En la línea que contiene `const_cast`, el tipo de datos del puntero `this` es `const CCTest *`. El operador `const_cast` cambia el tipo de datos del puntero `this` a `CCTest *`, lo que permite que se modifique el elemento `number` miembro. La conversión se produce únicamente para el resto de la instrucción en la que aparece.  
  
## <a name="see-also"></a>Vea también  
 [Operadores de conversión](../cpp/casting-operators.md)   
 [Palabras clave](../cpp/keywords-cpp.md)