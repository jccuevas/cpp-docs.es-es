---
title: Error del compilador C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: a25c59fa5c9ba0102666f6c8922a61b063e7627a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202311"
---
# <a name="compiler-error-c2712"></a>Error del compilador C2712

> No se puede usar __try en funciones que requieran desenredo de objetos

## <a name="remarks"></a>Observaciones

El error C2712 puede producirse si se usa [/EHsc](../../build/reference/eh-exception-handling-model.md)y una función con control de excepciones estructurado también tiene objetos que requieren el desenredo (destrucción).

Posibles soluciones:

- Mueva el código que requiere SEH a otra función

- Vuelva a escribir las funciones que usan SEH para evitar el uso de variables locales y parámetros que tengan destructores. No usar SEH en constructores o destructores

- Compilar sin /EHsc

El error C2712 también puede producirse si se llama a un método declarado mediante la palabra clave [__event](../../cpp/event.md) . Dado que el evento podría usarse en un entorno multiproceso, el compilador genera código que impide la manipulación del objeto de evento subyacente y, a continuación, incluye el código generado en una [instrucción try-finally](../../cpp/try-finally-statement.md)de SEH. Por lo tanto, el error C2712 se producirá si llama al método de evento y pasa por valor un argumento cuyo tipo tiene un destructor. En este caso, una solución es pasar el argumento como referencia constante.

C2712 también se puede producir si se compila con **/clr: Pure** y se declara una matriz estática de punteros a funciones en un bloque de `__try`. Un miembro estático requiere que el compilador use la inicialización dinámica en **/clr: Pure**, lo que implica C++ el control de excepciones. Sin embargo, el control de excepciones de C++ no se permite en un bloque `__try`.

Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera el error C2712 y se muestra cómo corregirlo:

```cpp
// C2712.cpp
// compile with: /clr:pure /c
struct S1 {
   static int smf();
   void fnc();
};

void S1::fnc() {
   __try {
      static int (*array_1[])() = {smf,};   // C2712

      // OK
      static int (*array_2[2])();
      array_2[0] = smf;
    }
    __except(0) {}
}
```
