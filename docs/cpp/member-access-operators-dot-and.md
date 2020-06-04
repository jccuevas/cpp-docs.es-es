---
title: Operadores de acceso a miembros:. y-&gt;
ms.date: 11/04/2016
f1_keywords:
- .
- ->
helpviewer_keywords:
- member access, expressions
- operators [C++], member access
- dot operator (.)
- -> operator
- member access, operators
- postfix operators [C++]
- . operator
- member access
ms.assetid: f8fc3df9-d728-40c5-b384-276927f5f1b3
ms.openlocfilehash: 05bab55e1646783e0f8ab9b414d608c912f60a0f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178020"
---
# <a name="member-access-operators--and--gt"></a>Operadores de acceso a miembros:. y-&gt;

## <a name="syntax"></a>Sintaxis

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Observaciones

Los operadores de acceso a miembros **.** y **->** se usan para hacer referencia a los miembros de estructuras, uniones y clases. Las expresiones de acceso a miembros tienen el valor y el tipo del miembro seleccionado.

Hay dos formas de expresiones de acceso de miembro:

1. En el primer formulario, *postfijo-Expression* representa un valor de struct, Class o Union Type, y *Name* nombra un miembro de la estructura, Unión o clase especificadas. El valor de la operación es el de *Name* y es un valor l si *postfijo-Expression* es un valor l.

1. En el segundo formulario, *postfijo-Expression* representa un puntero a una estructura, Unión o clase, y *Name* nombra un miembro de la estructura, Unión o clase especificadas. El valor es el de *Name* y es un valor l. El operador **->** desreferencia el puntero. Por consiguiente, las expresiones `e->member` y `(*e).member` (donde *e* representa un puntero) producen resultados idénticos (excepto cuando los operadores **->** o <strong>\*</strong> están sobrecargados).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestran dos formas del operador de acceso a miembros.

```cpp
// expre_Selection_Operator.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

struct Date {
   Date(int i, int j, int k) : day(i), month(j), year(k){}
   int month;
   int day;
   int year;
};

int main() {
   Date mydate(1,1,1900);
   mydate.month = 2;
   cout  << mydate.month << "/" << mydate.day
         << "/" << mydate.year << endl;

   Date *mydate2 = new Date(1,1,2000);
   mydate2->month = 2;
   cout  << mydate2->month << "/" << mydate2->day
         << "/" << mydate2->year << endl;
   delete mydate2;
}
```

```Output
2/1/1900
2/1/2000
```

## <a name="see-also"></a>Consulte también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Clases y structs](../cpp/classes-and-structs-cpp.md)<br/>
[Miembros de estructura y de unión](../c-language/structure-and-union-members.md)
