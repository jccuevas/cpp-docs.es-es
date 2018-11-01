---
title: Paso de parámetros
ms.date: 11/04/2016
ms.assetid: e838ee5f-c2fe-40b0-9a23-8023c949c820
ms.openlocfilehash: 1b7fb126ab3b140d0ab672067df35c5fc8df926e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648752"
---
# <a name="parameter-passing"></a>Paso de parámetros

Los primeros cuatro argumentos de entero se pasan en registros. Se pasan valores enteros (en orden de izquierda a derecha) en RCX, RDX, R8 y R9. Cinco argumentos y superior se pasan en la pila. Todos los argumentos son justificado a la derecha en los registros. Esto se realiza por lo que el destinatario puede omitir los bits superiores del registro si tiene que ser y puede tener acceso a solo la parte del registro que necesita.

Argumentos de punto flotante y precisión doble que se pasan en XMM0: XMM3 (hasta 4) con la ranura de entero (RCX, RDX, R8 y R9) que se usan normalmente para esa ranura cardinal que se va a omitir (vea el ejemplo) y viceversa.

[__m128](../cpp/m128.md) tipos, matrices y cadenas nunca se pasan por valor inmediato, pero en su lugar se pasa un puntero a la memoria asignada por el llamador. Los structs o uniones de tamaño 8, 16, 32 o 64 bits y __m64 se pasan como si fueran enteros del mismo tamaño. Los structs o uniones de tamaños distintos a estos se pasan como un puntero a la memoria asignada por el llamador. Para estos tipos de agregado se pasa como un puntero (incluidos \__m128), la memoria temporal asignada por el llamador será la alineación de 16 bytes.

Funciones intrínsecas que no asignan espacio de pila y no llame a otras funciones pueden usar otros registros variables para pasar argumentos de registro adicionales porque no hay un fuerte enlace entre el compilador y la implementación de la función intrínseca. Esta es una oportunidad adicional para mejorar el rendimiento.

El destinatario tiene la responsabilidad de volcar los parámetros de registro en su espacio de sombra si es necesario.

En la tabla siguiente se resume cómo se pasan los parámetros:

|Tipo de parámetro|Cómo se pasa|
|--------------------|----------------|
|Punto flotante|4 primeros parámetros - XMM0 a XMM3. Otros se pasan en la pila.|
|Integer|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|
|Agregados (8, 16, 32 o 64 bits) y __m64|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|
|Agregados (otros)|Por el puntero. En primer lugar 4 parámetros se pasan como punteros en RCX, RDX, R8 y R9|
|__m128|Por el puntero. En primer lugar 4 parámetros se pasan como punteros en RCX, RDX, R8 y R9|

## <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo del paso 1: todos los enteros de argumentos

```
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

## <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo del paso 2: todos los valores de punto flotante de argumentos

```
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

## <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo del paso 3: enteros y flotantes combinados de argumentos

```
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

## <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Ejemplo del paso 4 de argumentos-__m64, \__m128 y agregados

```
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)