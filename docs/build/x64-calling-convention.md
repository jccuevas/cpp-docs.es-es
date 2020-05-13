---
title: Convención de llamadas x64
description: Detalles de la convención de llamada ABI x64 predeterminada.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335124"
---
# <a name="x64-calling-convention"></a>Convención de llamadas x64

En esta sección se describen los procesos y convenciones estándar que una función (el autor de la llamada) utiliza para realizar llamadas a otra función (el destinatario) en código x64.

## <a name="calling-convention-defaults"></a>Llamadas predeterminadas de convención

La interfaz binaria de aplicación (ABI) x64 utiliza una convención de llamada rápida de cuatro registros de forma predeterminada. El espacio se asigna en la pila de llamadas como un almacén de sombras para que los destinatarios guarden esos registros. Hay una correspondencia estricta uno a uno entre los argumentos de una llamada de función y los registros utilizados para esos argumentos. Cualquier argumento que no cabe en 8 bytes o que no sea de 1, 2, 4 u 8 bytes, debe pasarse por referencia. Un solo argumento nunca se distribuye entre varios registros. La pila de registros x87 no se utiliza y puede ser utilizada por el destinatario de la llamada, pero debe considerarse volátil entre las llamadas de función. Todas las operaciones de punto flotante se realizan utilizando los 16 registros XMM. Los argumentos enteros se pasan en los registros RCX, RDX, R8 y R9. Los argumentos de punto flotante se pasan en XMM0L, XMM1L, XMM2L y XMM3L. Los argumentos de 16 bytes se pasan por referencia. El paso de parámetros se describe en detalle en [Paso de parámetros](#parameter-passing). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. Todos los demás registros no son volátiles. El uso del registro se documenta en detalle en [Registrar uso](../build/x64-software-conventions.md#register-usage) y Registros guardados de [llamadas/destinatarios.](#callercallee-saved-registers)

Para las funciones prototipo, todos los argumentos se convierten a los tipos de destinatario esperados antes de pasar. El autor de la llamada es responsable de asignar espacio para los parámetros al destinatario de la llamada y siempre debe asignar espacio suficiente para almacenar cuatro parámetros de registro, incluso si el destinatario no toma tantos parámetros. Esta convención simplifica la compatibilidad con funciones de lenguaje C sin prototipo y funciones vararg C/C++. Para las funciones vararg o no prototipo, los valores de punto flotante deben duplicarse en el registro de uso general correspondiente. Cualquier parámetro más allá de los cuatro primeros debe almacenarse en la pila después del almacén de sombras antes de la llamada. Los detalles de la función Vararg se pueden encontrar en [Varargs](#varargs). La información de la función sin prototipos se detalla en [Funciones](#unprototyped-functions)no prototipo .

## <a name="alignment"></a>Alignment

La mayoría de las estructuras están alineadas con su alineación natural. Las excepciones principales son `malloc` el `alloca` puntero de pila o la memoria, que se alinean a 16 bytes para ayudar al rendimiento. La alineación por encima de 16 bytes debe realizarse manualmente, pero dado que 16 bytes es un tamaño de alineación común para las operaciones XMM, este valor debe funcionar para la mayoría del código. Para obtener más información sobre el diseño y la alineación de la estructura, vea [Tipos y almacenamiento](../build/x64-software-conventions.md#types-and-storage). Para obtener información sobre el diseño de la pila, consulte uso de la [pila x64](../build/stack-usage.md).

## <a name="unwindability"></a>Desenredo

Las funciones hoja son funciones que no cambian ningún registro no volátil. Una función no hoja puede cambiar RSP no volátil, por ejemplo, llamando a una función o asignando espacio de pila adicional para variables locales. Para recuperar registros no volátiles cuando se controla una excepción, las funciones no hoja deben anotarse con datos estáticos que describen cómo desenredar correctamente la función en una instrucción arbitraria. Estos datos se almacenan como *datos pdata*o de procedimiento, que a su vez se refiere a *xdata*, los datos de control de excepciones. Los xdata contienen la información de desenredado y pueden apuntar a pdata adicional o una función de controlador de excepciones. Los prologs y los epílogos están muy restringidos para que se puedan describir correctamente en xdata. El puntero de pila debe estar alineado a 16 bytes en cualquier región de código que no forme parte de un epílogo o prólogo, excepto dentro de las funciones hoja. Las funciones hoja se pueden desenrollar simplemente simulando un retorno, por lo que pdata y xdata no son necesarios. Para obtener más información sobre la estructura adecuada de los prólogos y epílogos de funciones, véase [el prólogo y el epílogo x64.](../build/prolog-and-epilog.md) Para obtener más información sobre el control de excepciones y el control y desenredado de excepciones de pdata y xdata, vea control de [excepciones x64.](../build/exception-handling-x64.md)

## <a name="parameter-passing"></a>Paso de parámetros

Los primeros cuatro argumentos enteros se pasan en registros. Los valores enteros se pasan en orden de izquierda a derecha en RCX, RDX, R8 y R9, respectivamente. Los argumentos cinco y superiores se pasan en la pila. Todos los argumentos están justificados a la derecha en los registros, por lo que el destinatario puede ignorar los bits superiores del registro y acceder solo a la parte del registro necesaria.

Los argumentos de punto flotante y de doble precisión en los primeros cuatro parámetros se pasan en XMM0 - XMM3, dependiendo de la posición. Los registros enteros RCX, RDX, R8 y R9 que normalmente se usarían para esas posiciones se omiten, excepto en el caso de los argumentos varargs. Para obtener más información, consulte [Varargs](#varargs). De forma similar, los registros XMM0 - XMM3 se omiten cuando el argumento correspondiente es un tipo entero o puntero.

[__m128](../cpp/m128.md) tipos, matrices y cadenas nunca se pasan por valor inmediato. En su lugar, un puntero se pasa a la memoria asignada por el autor de la llamada. Las estructuras y uniones de tamaño 8, 16, 32 o 64 bits y __m64 tipos se pasan como si fueran enteros del mismo tamaño. Las estructuras o uniones de otros tamaños se pasan como un puntero a la memoria asignada por el autor de la llamada. Para estos tipos agregados pasados como puntero, incluido \__m128, la memoria temporal asignada por el autor de la llamada debe estar alineada de 16 bytes.

Las funciones intrínsecas que no asignan espacio de pila y no llaman a otras funciones, a veces usan otros registros volátiles para pasar argumentos de registro adicionales. Esta optimización es posible gracias al enlace estrecho entre el compilador y la implementación de la función intrínseca.

El destinatario es responsable de volcar los parámetros de registro en su espacio de sombra si es necesario.

En la tabla siguiente se resume cómo se pasan los parámetros:

|Tipo de parámetro|Cómo pasó|
|--------------------|----------------|
|Punto flotante|Primeros 4 parámetros - XMM0 a XMM3. Otros pasaron en la pila.|
|Entero|Primeros 4 parámetros - RCX, RDX, R8, R9. Otros pasaron en la pila.|
|Agregados (8, 16, 32 o 64 bits) y __m64|Primeros 4 parámetros - RCX, RDX, R8, R9. Otros pasaron en la pila.|
|Agregados (otros)|Por puntero. Los primeros 4 parámetros pasados como punteros en RCX, RDX, R8 y R9|
|__m128|Por puntero. Los primeros 4 parámetros pasados como punteros en RCX, RDX, R8 y R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo de argumento que pasa 1 - todos los enteros

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo de argumento que pasa 2 - todos los flotadores

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo de argumento que pasa 3 - ints y flotadores mixtos

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Ejemplo de argumento que \_pasa 4 -__m64, _m128 y agregados

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, argumentos de puntos suspensivos), se aplica la convención de paso de parámetros de registro normal, incluido el derramamiento de los argumentos quinto y posteriores a la pila. Es responsabilidad del destinatario volcar los argumentos que tienen su dirección tomada. Solo para valores de punto flotante, tanto el registro entero como el registro de punto flotante deben contener el valor, en caso de que el destinatario espere el valor en los registros enteros.

## <a name="unprototyped-functions"></a>Funciones no prototipo

Para las funciones que no están completamente prototipos, el llamador pasa valores enteros como enteros y valores de punto flotante como precisión doble. Solo para valores de punto flotante, tanto el registro entero como el registro de punto flotante contienen el valor float en caso de que el destinatario espere el valor en los registros enteros.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valores devueltos

Un valor devuelto escalar que puede caber en 64 bits se devuelve a través de RAX; esto incluye tipos de __m64. Tipos no escalares, incluidos floats, doubles y tipos vectoriales como [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) se devuelven en XMM0. El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.

Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas. Para devolver un tipo definido por el usuario por valor en RAX, debe tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits. También debe tener ningún constructor definido por el usuario, destructor o operador de asignación de copia; no hay miembros de datos no estáticos privados o protegidos; no hay miembros de datos no estáticos de tipo de referencia; no hay clases base; sin funciones virtuales; y no hay miembros de datos que no cumplan también estos requisitos. (Esto es esencialmente la definición de un tipo POD de C++03. Dado que la definición ha cambiado en el estándar C++11, no se recomienda usar `std::is_pod` para esta prueba.) De lo contrario, el autor de la llamada asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como el primer argumento. Los argumentos subsiguientes se desplazan entonces un argumento a la derecha. El destinatario debe devolver el mismo puntero en RAX.

Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:

### <a name="example-of-return-value-1---64-bit-result"></a>Ejemplo del valor devuelto 1 - 64 bits resultado

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Ejemplo del valor devuelto 2 - 128 bits resultado

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Ejemplo del valor devuelto 3 - resultado del tipo de usuario por puntero

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Ejemplo del valor devuelto 4 - resultado del tipo de usuario por valor

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registros guardados de llamadas/destinatarios

Los registros RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 y las partes superiores de YMM0-15 y ZMM0-15 se consideran volátiles y deben considerarse destruidos en llamadas de función (a menos que se pueda obtener de otra manera la seguridad mediante análisis como la optimización de todo el programa). En AVX512VL, los registros ZMM, YMM y XMM 16-31 son volátiles.

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 y XMM6-15 se consideran no volátiles y deben guardarse y restaurarse mediante una función que los utilice.

## <a name="function-pointers"></a>Punteros de función

Los punteros de función son simplemente punteros a la etiqueta de la función respectiva. No hay requisitos de tabla de contenido (TOC) para punteros de función.

## <a name="floating-point-support-for-older-code"></a>Soporte de punto flotante para código antiguo

Los registros de pila MMX y de punto flotante (MM0-MM7/ST0-ST7) se conservan en todos los switches de contexto. No hay ninguna convención de llamada explícita para estos registros. El uso de estos registros está estrictamente prohibido en el código del modo kernel.

## <a name="fpcsr"></a>FpCsr

El estado de registro también incluye la palabra de control FPU x87. La convención de llamada dicta que este registro no sea volátil.

El registro de palabras de control FPU x87 se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registrar\[bits] | Configuración |
|-|-|
| FPCSR\[0:6] | La excepción enmascara todos los 1 (todas las excepciones enmascaradas) |
| FPCSR\[7] | Reservado - 0 |
| FPCSR\[8:9] | Control de precisión - 10B (doble precisión) |
| FPCSR\[10:11] | Control de redondeo - 0 (redondo a más cercano) |
| FPCSR\[12] | Control infinito - 0 (no utilizado) |

Un destinatario que modifica cualquiera de los campos dentro de FPCSR debe restaurarlos antes de volver a su llamador. Además, un llamador que ha modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar un destinatario de llamadas a menos que por acuerdo el destinatario espera los valores modificados.

Hay dos excepciones a las reglas sobre la no volatilidad de los indicadores de control:

1. En funciones donde el propósito documentado de la función dada es modificar los indicadores FpCsr no volátiles.

1. Cuando es posible que sea correcto que la violación de estas reglas da como resultado un programa que se comporta igual que un programa donde estas reglas no se violan, por ejemplo, a través del análisis de todo el programa.

## <a name="mxcsr"></a>MxCsr

El estado de registro también incluye MxCsr. La convención de llamada divide este registro en una parte volátil y una parte no volátil. La parte volátil consiste en los seis indicadores de estado, en\[MXCSR\[0:5], mientras que el resto del registro, MXCSR 6:15], se considera no volátil.

La parte no volátil se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registrar\[bits] | Configuración |
|-|-|
| MXCSR\[6] | Los denormales son ceros - 0 |
| MXCSR\[7:12] | La excepción enmascara todos los 1 (todas las excepciones enmascaradas) |
| MXCSR\[13:14] | Control de redondeo - 0 (redondo a más cercano) |
| MXCSR\[15] | Flush a cero para subflujo enmascarado - 0 (desactivado) |

Un destinatario que modifica cualquiera de los campos no volátiles dentro de MXCSR debe restaurarlos antes de volver a su llamador. Además, un llamador que ha modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar un destinatario de llamadas a menos que por acuerdo el destinatario espera los valores modificados.

Hay dos excepciones a las reglas sobre la no volatilidad de los indicadores de control:

- En las funciones donde el propósito documentado de la función dada es modificar los indicadores MxCsr no volátiles.

- Cuando es posible que sea correcto que la violación de estas reglas da como resultado un programa que se comporta igual que un programa donde estas reglas no se violan, por ejemplo, a través del análisis de todo el programa.

No se pueden hacer suposiciones sobre el estado de la parte volátil de MXCSR a través de un límite de función, a menos que se describa específicamente en la documentación de una función.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Cuando se incluye setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o `__finally` [longjmp](../c-runtime-library/reference/longjmp.md) dan como resultado un desenredado que invoca destructores y llamadas.  Esto difiere de x86, donde incluir setjmp.h da como resultado `__finally` cláusulas y destructores que no se invocan.

Una llamada `setjmp` para conservar el puntero de pila actual, los registros no volátiles y los registros MxCsr.  Llamadas `longjmp` para volver `setjmp` al sitio de llamada más reciente y restablece el puntero de pila, registros no volátiles y registros MxCsr, de nuevo al estado conservado por la llamada más reciente. `setjmp`

## <a name="see-also"></a>Consulte también

[Convenciones de software x64](../build/x64-software-conventions.md)
