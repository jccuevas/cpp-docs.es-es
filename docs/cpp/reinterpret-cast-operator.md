---
title: reinterpret_cast (Operador)
ms.date: 11/04/2016
f1_keywords:
- reinterpret_cast_cpp
helpviewer_keywords:
- reinterpret_cast keyword [C++]
ms.assetid: eb3283c7-7f88-467e-affd-407d37b46d6c
ms.openlocfilehash: 34c2fcb0e1f7f4df4e207d1737afc9c42e011feb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188290"
---
# <a name="reinterpret_cast-operator"></a>reinterpret_cast (Operador)

Permite que cualquier puntero se convierta en cualquier otro tipo de puntero. También permite convertir cualquier tipo entero en cualquier tipo de puntero y viceversa.

## <a name="syntax"></a>Sintaxis

```
reinterpret_cast < type-id > ( expression )
```

## <a name="remarks"></a>Observaciones

El uso incorrecto del operador **reinterpret_cast** puede ser fácilmente no seguro. A menos que la conversión deseada sea inherentemente de bajo nivel, se debe utilizar uno de los otros operadores de conversión.

El operador **reinterpret_cast** se puede usar para conversiones como `char*` a `int*`o `One_class*` a `Unrelated_class*`, que son intrínsecamente inseguras.

El resultado de una **reinterpret_cast** no puede usarse de forma segura para ningún elemento que no sea una conversión a su tipo original. Otros usos son, en el mejor de los casos, no portables.

El operador **reinterpret_cast** no puede desechar los atributos **const**, **volatile**o **__unaligned** . Consulte [Const_cast operador](../cpp/const-cast-operator.md) para obtener información sobre cómo quitar estos atributos.

El operador **reinterpret_cast** convierte un valor de puntero nulo en el valor de puntero nulo del tipo de destino.

Un uso práctico de **reinterpret_cast** está en una función hash, que asigna un valor a un índice de tal forma que dos valores distintos raramente terminan con el mismo índice.

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

## <a name="see-also"></a>Consulte también

[Operadores de conversión](../cpp/casting-operators.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
