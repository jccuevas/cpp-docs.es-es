---
title: reinterpret_cast (operador) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- reinterpret_cast_cpp
dev_langs:
- C++
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bd11dee65d020fdc1fb9f6702e675e807b0f61ab
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067484"
---
# <a name="reinterpretcast-operator"></a>reinterpret_cast (Operador)

Permite que cualquier puntero se convierta en cualquier otro tipo de puntero. También permite convertir cualquier tipo entero en cualquier tipo de puntero y viceversa.

## <a name="syntax"></a>Sintaxis

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Comentarios

Uso incorrecto de la **reinterpret_cast** operador puede ser no seguro. A menos que la conversión deseada sea inherentemente de bajo nivel, se debe utilizar uno de los otros operadores de conversión.

El **reinterpret_cast** operador puede usarse para las conversiones como `char*` a `int*`, o `One_class*` a `Unrelated_class*`, que son intrínsecamente no seguras.

El resultado de una **reinterpret_cast** con seguridad no se puede usar para algo distinto que convertirlo a su tipo original. Otros usos son, en el mejor de los casos, no portables.

El **reinterpret_cast** operador no se puede desechar el **const**, **volátil**, o **__unaligned** atributos. Consulte [const_cast (operador)](../cpp/const-cast-operator.md) para obtener información acerca de cómo quitar estos atributos.

El **reinterpret_cast** operador convierte un valor de puntero nulo en el valor de puntero null del tipo de destino.

Un uso práctico de **reinterpret_cast** está en una función hash, que se asigna un valor a un índice de tal manera que dos distintos valores rara vez final copia con el mismo índice.

```cpp
#include <iostream>
using namespace std;

// Returns a hash code based on an address
unsigned short Hash( void *p ) {
   unsigned int val = reinterpret_cast<unsigned int>( p );
   return ( unsigned short )( val ^ (val >> 16));
}

using namespace std;
int main() {
   int a[20];
   for ( int i = 0; i < 20; i++ )
      cout << Hash( a + i ) << endl;
}

Output:
64641
64645
64889
64893
64881
64885
64873
64877
64865
64869
64857
64861
64849
64853
64841
64845
64833
64837
64825
64829
```

El **reinterpret_cast** permite que el puntero se trate como un tipo entero. El resultado se cambia a bits y se compara mediante XOR consigo mismo para producir un índice único (con un alto grado de probabilidad). El índice se trunca mediante una conversión de estilo de C al tipo de valor devuelto de la función.

## <a name="see-also"></a>Vea también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)