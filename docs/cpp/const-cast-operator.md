---
title: const_cast (Operador)
ms.date: 11/04/2016
f1_keywords:
- const_cast_cpp
helpviewer_keywords:
- const_cast keyword [C++]
ms.assetid: 4d8bb203-ef33-4a10-9f9f-c64d4fbc1687
ms.openlocfilehash: d2711142e4aa73cc0119949876e7e593067cd45d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180347"
---
# <a name="const_cast-operator"></a>const_cast (Operador)

Quita los atributos **const**, **volatile**y **__unaligned** de una clase.

## <a name="syntax"></a>Sintaxis

```
const_cast <type-id> (expression)
```

## <a name="remarks"></a>Observaciones

Un puntero a cualquier tipo de objeto o un puntero a un miembro de datos se puede convertir explícitamente en un tipo que es idéntico, salvo los calificadores **const**, **volatile**y **__unaligned** . Para los punteros y las referencias, el resultado hará referencia al objeto original. Para los punteros a miembros de datos, el resultado hará referencia al mismo miembro que el puntero original (sin convertir) al miembro de datos. Según el tipo del objeto al que se hace referencia, una operación de escritura a través del puntero, referencia o puntero a miembro de datos resultante podría generar un comportamiento indefinido.

No se puede usar el operador **const_cast** para invalidar directamente el estado constante de una variable de constante.

El operador **const_cast** convierte un valor de puntero nulo en el valor de puntero nulo del tipo de destino.

## <a name="example"></a>Ejemplo

```cpp
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

En la línea que contiene el **const_cast**, el tipo de datos del puntero **this** es `const CCTest *`. El operador **const_cast** cambia el tipo de datos del puntero **this** a `CCTest *`, lo que permite modificar el miembro `number`. La conversión se produce únicamente para el resto de la instrucción en la que aparece.

## <a name="see-also"></a>Consulte también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
