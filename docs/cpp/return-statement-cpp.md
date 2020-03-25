---
title: return (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: c8ea796ab40a2090ed9853377f7c9415914bc0e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178987"
---
# <a name="return-statement-c"></a>return (Instrucción) (C++)

Finaliza la ejecución de una función y devuelve el control a la función de llamada (o al sistema operativo si se transfiere el control de la función `main`). La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada.

## <a name="syntax"></a>Sintaxis

```
return [expression];
```

## <a name="remarks"></a>Observaciones

La cláusula `expression`, si está presente, se convierte al tipo especificado en la declaración de función, como si se realizara una inicialización. La conversión del tipo de la expresión al tipo de **valor devuelto** de la función puede crear objetos temporales. Para obtener más información sobre cómo y cuándo se crean objetos temporales, vea [objetos temporales](../cpp/temporary-objects.md).

El valor de la cláusula `expression` se devuelve a la función de llamada. Si se omite la expresión, el valor devuelto de la función es indefinido. Los constructores y destructores, y las funciones de tipo **void**, no pueden especificar una expresión en la instrucción **Return** . Las funciones de todos los demás tipos deben especificar una expresión en la instrucción **Return** .

Cuando el flujo de control sale del bloque que contiene la definición de función, el resultado es el mismo que si se hubiera ejecutado una instrucción **Return** sin una expresión. Esto no es válido para las funciones que se declaran como si devolvieran un valor.

Una función puede tener cualquier número de instrucciones **Return** .

En el ejemplo siguiente se usa una expresión con una instrucción **Return** para obtener el mayor de dos enteros.

## <a name="example"></a>Ejemplo

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>Consulte también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
