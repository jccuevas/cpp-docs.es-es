---
title: Operadores de acceso a miembro:. y -&gt; | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- .
- ->
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c02183b3dc03c785ef5a6a08da80dd8435288b0a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112777"
---
# <a name="member-access-operators--and--gt"></a>Operadores de acceso a miembro:. y -&gt;

## <a name="syntax"></a>Sintaxis

```
postfix-expression . name
postfix-expression -> name
```

## <a name="remarks"></a>Comentarios

Los operadores de acceso de miembro **.** y **->** se usan para hacer referencia a los miembros de estructuras, uniones y clases. Las expresiones de acceso a miembros tienen el valor y el tipo del miembro seleccionado.

Hay dos formas de expresiones de acceso de miembro:

1. En la primera forma, *postfix-expression* representa un valor de tipo de unión, clase o struct y *nombre* nombra un miembro de la estructura especificada, unión o clase. El valor de la operación es de *nombre* y es un valor l si *postfix-expression* es un valor l.

1. En la segunda forma, *postfix-expression* representa un puntero a una estructura, unión o clase, y *nombre* nombra un miembro de la estructura especificada, unión o clase. El valor es el de *nombre* y es un valor l. El **->** operador de desreferencia el puntero. Por lo tanto, las expresiones `e->member` y `(*e).member` (donde *e* representa un puntero) producen resultados idénticos (excepto cuando los operadores **->** o <strong>\*</strong> están sobrecargados).

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

## <a name="see-also"></a>Vea también

[Expresiones postfijas](../cpp/postfix-expressions.md)<br/>
[Operadores integrados de C++, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[Clases y structs](../cpp/classes-and-structs-cpp.md)<br/>
[Miembros de estructura y de unión](../c-language/structure-and-union-members.md)