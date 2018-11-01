---
title: Error del compilador C2712
ms.date: 11/04/2016
f1_keywords:
- C2712
helpviewer_keywords:
- C2712
ms.assetid: f7d4ffcc-7ed2-459b-8067-a728ce647071
ms.openlocfilehash: 19b9c5a54bf405114bd4d596c2a2cc4708aadcc9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507918"
---
# <a name="compiler-error-c2712"></a>Error del compilador C2712

> No se puede usar __try en funciones que requieran desenredo de objetos

## <a name="remarks"></a>Comentarios

Error C2712 puede producirse si usa [/EHsc](../../build/reference/eh-exception-handling-model.md), y una función con control de excepciones estructurado también tiene objetos que requieran desenredo (destrucción).

Soluciones posibles:

- Mueva el código que requiere SEH a otra función

- Vuelva a escribir las funciones que usan SEH para evitar el uso de variables locales y parámetros que tengan destructores. No usar SEH en constructores o destructores

- Compilar sin /EHsc

Error C2712 puede producirse también si se llama a un método declarado mediante la [__event](../../cpp/event.md) palabra clave. Dado que el evento podría utilizarse en un entorno multiproceso, el compilador genera código que impide la manipulación del objeto de evento subyacente y, a continuación, agrega el código generado en una SEH [instrucción try-finally](../../cpp/try-finally-statement.md). Por lo tanto, el error C2712 se producirá si llama al método de evento y pasa por valor un argumento cuyo tipo tiene un destructor. En este caso, una solución es pasar el argumento como referencia constante.

Error C2712 también se puede producir si se compila con **/CLR: pure** y declarar una matriz estática de punteros a funciones en un `__try` bloque. Un miembro estático exige al compilador que use la inicialización dinámica en **/CLR: pure**, lo que implica el control de excepciones de C++. Sin embargo, el control de excepciones de C++ no se permite en un bloque `__try`.

El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

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