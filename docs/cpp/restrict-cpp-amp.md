---
title: restrict (C++ AMP)
ms.date: 11/04/2016
f1_keywords:
- cpu_CPP
- amp_CPP
helpviewer_keywords:
- restrict clause (C++ AMP)
ms.assetid: 07d3291f-7edf-456b-8828-283ac8673661
ms.openlocfilehash: 5a0011d11e4a59c9ca3a5e18f44d4cf831b21582
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366654"
---
# <a name="restrict-c-amp"></a>restrict (C++ AMP)

El especificador de restricción se puede aplicar a declaraciones de función y lambda. Impone restricciones en el código de la función y en el comportamiento de la función en aplicaciones que utilizan el runtime C++ Accelerated Massive Parallelism (C++ AMP).

> [!NOTE]
> Para obtener información acerca de la palabra clave **restrict** que forma parte de la **__declspec** atributos de clase de almacenamiento, consulte [restrict](../cpp/restrict.md).

La cláusula **restrict** adopta las siguientes formas:

|Cláusula|Descripción|
|------------|-----------------|
|`restrict(cpu)`|La función puede usar el lenguaje de C++ completo. Solo otras funciones declaradas mediante funciones restrict(cpu) pueden llamar a la función.|
|`restrict(amp)`|La función solo puede usar el subconjunto del lenguaje C++ que C++ AMP pueda acelerar.|
|Secuencia de `restrict(cpu)` y `restrict(amp)`.|La función debe cumplir las limitaciones de `restrict(cpu)` y `restrict(amp)`. La función puede ser objeto de llamadas desde funciones declaradas mediante `restrict(cpu)`, `restrict(amp)`, `restrict(cpu, amp)` o `restrict(amp, cpu)`.<br /><br /> La forma `restrict(A) restrict(B)` puede escribirse como `restrict(A,B)`.|

## <a name="remarks"></a>Observaciones

La palabra clave **restrict** es una palabra clave contextual. Los especificadores de restricción `cpu` y `amp` no son palabras reservadas. La lista de especificadores no es extensible. Una función que no tiene una cláusula **restrict** es `restrict(cpu)` la misma que una función que tiene la cláusula.

Una función que incluye la cláusula `restrict(amp)` tiene las siguientes limitaciones:

- La función puede llamar solo a funciones que tengan la cláusula `restrict(amp)`.

- La función se debe poder insertar.

- La función solo puede declarar variables **int**, **unsigned int**, **float**y **double,** y clases y estructuras que contienen solo estos tipos. **Bool** también está permitido, pero debe estar alineado con 4 bytes si se utiliza en un tipo compuesto.

- Las funciones lambda no pueden capturar por referencia, y no pueden capturar punteros.

- Las referencias y los punteros de un solo direccionamiento indirecto se admiten únicamente como variables locales, argumentos de función y tipos de valor devuelto.

- No se permite lo siguiente:

  - La recursividad.

  - Variables declaradas con la palabra clave [volatile.](../cpp/volatile-cpp.md)

  - Funciones virtuales.

  - Punteros a funciones.

  - Punteros a funciones miembro.

  - Punteros en estructuras.

  - Punteros a punteros.

  - declaraciones **goto.**

  - Instrucciones con etiqueta.

  - **try**, **catch**o **throw** instrucciones.

  - Variables globales.

  - Variables estáticas. Utilice [tile_static palabra clave](../cpp/tile-static-keyword.md) en su lugar.

  - **dynamic_cast** yeso.

  - El operador **typeid.**

  - Declaraciones asm.

  - Varargs.

Para obtener una explicación de las limitaciones de funciones, consulte [Restringir (amp) Restricciones](https://blogs.msdn.microsoft.com/nativeconcurrency/2011/12/19/restrictamp-restrictions-part-0-of-n-introduction/).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente `restrict(amp)`se muestra cómo utilizar la cláusula.

```cpp
void functionAmp() restrict(amp) {}
void functionNonAmp() {}

void callFunctions() restrict(amp)
{
    // int is allowed.
    int x;
    // long long int is not allowed in an amp-restricted function. This generates a compiler error.
    // long long int y;

    // Calling an amp-restricted function is allowed.
    functionAmp();

    // Calling a non-amp-restricted function is not allowed.
    // functionNonAmp();
}
```

## <a name="see-also"></a>Consulte también

[C++ AMP (C++ Accelerated Massive Parallelism)](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)
