---
title: Funciones recursivas
ms.date: 11/04/2016
helpviewer_keywords:
- functions [C], recursive
- function calls, recursive
- functions [C], calling recursively
- recursive function calls
ms.assetid: 59739040-3081-4006-abbc-9d8423992bce
ms.openlocfilehash: 82f0c820ab75fda4bae83db78fa402d7a07cb7fe
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152435"
---
# <a name="recursive-functions"></a>Funciones recursivas

En un programa de C, se puede llamar a cualquier función de forma recursiva, es decir, cualquier función se puede llamar a sí misma. El número de llamadas recursivas viene limitado por el tamaño de la pila. Vea la opción del vinculador [/STACK (asignaciones de pila)](../build/reference/stack-stack-allocations.md) (/STACK) para obtener información sobre las opciones del vinculador que establecen el tamaño de la pila. Cada vez que se llama a la función, se asigna nuevo almacenamiento para los parámetros y para las variables **auto** y **register** para que no se sobrescriban sus valores en llamadas anteriores que no han finalizado. Los parámetros solo son accesibles directamente para la instancia de la función en la que se crean. Los parámetros anteriores no son directamente accesibles para las siguientes instancias de la función.

Tenga en cuenta que las variables declaradas con almacenamiento **static** no requieren nuevo almacenamiento con cada llamada recursiva. Su almacenamiento existe durante la vigencia del programa. Cada referencia a estas variables accede a la misma área de almacenamiento.

## <a name="example"></a>Ejemplo

En este ejemplo se ilustran las llamadas recursivas:

```C
int factorial( int num );      /* Function prototype */

int main()
{
    int result, number;
    .
    .
    .
    result = factorial( number );
}

int factorial( int num )      /* Function definition */
{
    .
    .
    .
    if ( ( num > 0 ) || ( num <= 10 ) )
        return( num * factorial( num - 1 ) );
}
```

## <a name="see-also"></a>Vea también

[Llamadas de función](../c-language/function-calls.md)
