---
title: return (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 47bf9c50a2da039b0ffa074796a768290b732bb3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507203"
---
# <a name="return-statement-c"></a>return (Instrucción) (C++)

Finaliza la ejecución de una función y devuelve el control a la función de llamada (o al sistema operativo si se transfiere el control de la función `main`). La ejecución se reanuda en la función de llamada, en el punto que sigue inmediatamente a la llamada.

## <a name="syntax"></a>Sintaxis

```
return [expression];
```

## <a name="remarks"></a>Comentarios

La cláusula `expression`, si está presente, se convierte al tipo especificado en la declaración de función, como si se realizara una inicialización. Conversión del tipo de la expresión a la **devolver** tipo de la función puede crear objetos temporales. Para obtener más información acerca de cómo y cuándo se crean objetos temporales, vea [objetos temporales](../cpp/temporary-objects.md).

El valor de la cláusula `expression` se devuelve a la función de llamada. Si se omite la expresión, el valor devuelto de la función es indefinido. Los constructores y destructores y funciones de tipo **void**, no se puede especificar una expresión en el **devolver** instrucción. Las funciones de todos los demás tipos deben especificar una expresión en el **devolver** instrucción.

Cuando el flujo de control sale del bloque que incluye la definición de función, el resultado es el mismo, como sería si un **devolver** hubiera ejecutado la instrucción sin una expresión. Esto no es válido para las funciones que se declaran como si devolvieran un valor.

Una función puede tener cualquier número de **devolver** instrucciones.

En el ejemplo siguiente se usa una expresión con un **devolver** instrucción para obtener el mayor de dos enteros.

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

## <a name="see-also"></a>Vea también

[Instrucciones de salto](../cpp/jump-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)