---
title: Convención de llamadas x64
description: Detalles de la convención de llamada predeterminada de la ABI de x64.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: caf22172ea5e9c20280bce8e508d72fd30c00c5b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335124"
---
# <a name="x64-calling-convention"></a>Convención de llamadas x64

En esta sección se describen los procesos y convenciones estándar que usa una función (autor de la llamada) para realizar llamadas en otra función (destinatario) en código x64.

## <a name="calling-convention-defaults"></a>Valor predeterminado de la convención de llamada

De forma predeterminada, la interfaz binaria de aplicación (ABI) x64 utiliza una Convención de llamada rápida de cuatro registros. Se asigna espacio en la pila de llamadas como un almacén de propiedades reemplazadas para que los destinatarios puedan guardar esos registros. Hay una correspondencia uno a uno estricta entre los argumentos de una llamada de función y los registros utilizados para esos argumentos. Cualquier argumento que no se ajuste a 8 bytes, o que no sea 1, 2, 4 u 8 bytes, debe pasarse por referencia. Un único argumento nunca se distribuye entre varios registros. La pila de registro de x87 está sin usar y el destinatario la puede utilizar, pero se debe considerar volátil entre las llamadas de función. Todas las operaciones de punto flotante se realizan mediante los 16 registros de XMM. Los argumentos de entero se pasan en los registros RCX, RDX, R8 y R9. Los argumentos de punto flotante se pasan en XMM0L, XMM1L, XMM2L y XMM3L. Los argumentos de 16 bytes se pasan por referencia. El paso de parámetros se describe en detalle en la sección [Paso de parámetros](#parameter-passing). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. El resto de los registros son no volátiles. El uso de registros se documenta en detalle en [Uso de registros](../build/x64-software-conventions.md#register-usage) y [Registros guardados del autor y el destinatario de la llamada](#callercallee-saved-registers).

En el caso de las funciones con prototipo, todos los argumentos se convierten en los tipos de destinatarios esperados antes de pasar. El autor de la llamada es el responsable de asignar espacio para los parámetros al destinatario y siempre debe asignar espacio suficiente para almacenar cuatro parámetros de registro, incluso si este destinatario no toma tantos parámetros. Esta convención simplifica la compatibilidad con las funciones de lenguaje de C sin prototipo y las funciones vararg C/C++. En el caso de las funciones vararg o sin prototipo, los valores de punto flotante se deben duplicar en el registro de uso general correspondiente. Cualquier parámetro más allá de los cuatro primeros se debe almacenar en la pila después del almacén de propiedades reemplazadas antes de la llamada. Los detalles de la función vararg se pueden encontrar en [Varargs](#varargs). La información de funciones sin prototipo se detalla en [Funciones sin prototipo](#unprototyped-functions).

## <a name="alignment"></a>Alineación

La mayoría de las estructuras se alinean con su alineación natural. Las excepciones principales son el puntero de pila y la memoria `malloc` o `alloca`, que se alinean a 16 bytes para ayudar al rendimiento. La alineación por encima de 16 bytes se debe realizar manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones XMM, este valor debería funcionar para la mayoría del código. Para obtener más información sobre la alineación y el diseño de la estructura, vea [Tipos y almacenamiento](../build/x64-software-conventions.md#types-and-storage). Para obtener información sobre el diseño de pila, vea [Uso de las pilas x64](../build/stack-usage.md).

## <a name="unwindability"></a>Capacidad de desenredado

Las funciones de hoja son funciones que no cambian ningún registro no volátil. Una función que no sea de hoja puede cambiar un RSP no volátil, por ejemplo, llamando a una función o asignando espacio de pila adicional para las variables locales. Para recuperar registros no volátiles cuando se controla una excepción, las funciones que no son de hoja se deben anotar con datos estáticos que describen cómo desenredar correctamente la función en una instrucción arbitraria. Estos datos se almacenan como *pdata* o datos de procedimiento, que a su vez hacen referencia a *xdata*, los datos de control de excepciones. Los xdata contienen la información de desenredado y pueden apuntar a un pdata adicional o a una función de controlador de excepciones. Los prólogos y epílogos están muy restringidos, de tal forma que se puedan describir correctamente en xdata. El puntero de pila debe estar alineado a 16 bytes en cualquier región de código que no forme parte de un epílogo o prólogo, excepto en las funciones de hoja. Las funciones de hoja se pueden desenredar simplemente simulando una devolución, por lo que no se requieren pdata ni xdata. Para obtener más información sobre la estructura adecuada de los prólogos y epílogos de función, vea [Prólogo y epílogo x64](../build/prolog-and-epilog.md). Para obtener más información sobre el control de excepciones, así como del control de excepciones y el desenredado de pdata y xdata, vea [Control de excepciones x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Paso de parámetros

Los cuatro primeros argumentos de tipo entero se pasan en registros. Los valores enteros se pasan en orden, de izquierda a derecha, en RCX, RDX, R8 y R9, respectivamente. Los argumentos del cinco en adelante se pasan en la pila. Todos los argumentos están justificados a la derecha en los registros, por lo que el destinatario puede ignorar los bits superiores del registro y acceder solo a la parte del registro necesaria.

Los argumentos de punto flotante y de precisión doble de los cuatro primeros parámetros se pasan en XMM0-XMM3, en función de la posición. Los registros de entero RCX, RDX, R8 y R9, que normalmente se utilizarían para esas posiciones se ignoran, excepto en el caso de argumentos varargs. Para obtener información detallada, vea [Varargs](#varargs). Del mismo modo, los registros de XMM0-XMM3 se ignoran cuando el argumento correspondiente es un tipo entero o de puntero.

Los tipos de [__m128](../cpp/m128.md), las matrices y las cadenas nunca se pasan por valor inmediato. En su lugar, se pasa un puntero a la memoria que asigna el autor de la llamada. Las estructuras y uniones de tamaño 8, 16, 32 o 64 bits, y los tipos de __m64, se pasan como si fueran enteros del mismo tamaño. Las estructuras o uniones de otros tamaños se pasan como un puntero a la memoria que asigna el autor de la llamada. Para estos tipos de agregado que se pasan como puntero, incluido \__m128, la memoria temporal asignada por el autor de la llamada debe tener una alineación de 16 bytes.

Las funciones intrínsecas que no asignan espacio de pila y no llaman a otras funciones, a veces usan otros registros volátiles para pasar argumentos de registro adicionales. Esta optimización se realiza mediante el enlace estricto entre el compilador y la implementación de la función intrínseca.

El destinatario es el responsable de volcar los parámetros de registro en su espacio de propiedades reemplazadas, en caso necesario.

En la tabla siguiente se resume cómo se pasan los parámetros:

|Tipo de parámetro|Cómo se pasa|
|--------------------|----------------|
|Punto flotante|Primeros 4 parámetros: de XMM0 a XMM3. Otros que se pasan en la pila.|
|Integer|Primeros 4 parámetros: RCX, RDX, R8 y R9. Otros que se pasan en la pila.|
|Agregados (8, 16, 32 o 64 bits) y __m64|Primeros 4 parámetros: RCX, RDX, R8 y R9. Otros que se pasan en la pila.|
|Agregados (otros)|Por puntero. Primeros 4 parámetros que se pasan como punteros en RCX, RDX, R8 y R9|
|__m128|Por puntero. Primeros 4 parámetros que se pasan como punteros en RCX, RDX, R8 y R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo 1 de paso de argumentos: todos los enteros

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo 2 de paso de argumentos: todos los flotantes

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo 3 de paso de argumentos: los enteros y los flotantes combinados

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Ejemplo 4 de paso de argumentos: __m64, \__m128 y agregados

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, argumentos de puntos suspensivos), se aplica la convención normal de paso de los parámetros de registro, incluido el volcado del quinto y de los argumentos siguientes en la pila. Es responsabilidad del destinatario volcar los argumentos que tienen su dirección tomada. Solo para los valores de punto flotante, tanto el registro de entero como el de punto flotante deben contener el valor, en caso de que el destinatario espere el valor de los registros enteros.

## <a name="unprototyped-functions"></a>Funciones sin prototipo

En el caso de las funciones sin prototipo completo, el autor de la llamada pasa valores enteros como enteros y valores de punto flotante como precisión doble. Solo para los valores de punto flotante, tanto el registro de entero como el de punto flotante contienen el valor flotante, en caso de que el destinatario espere el valor de los registros enteros.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valores devueltos

Un valor escalar devuelto que puede caber en 64 bits se devuelve mediante RAX. Esto incluye tipos __m64. Se devuelven tipos no escalares, incluidos tipos flotantes, dobles y de vector como [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) y [__m128d](../cpp/m128d.md) en XMM0. El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.

Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas. Para devolver un tipo definido por el usuario por valor en RAX, debe tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits. También es necesario que no tenga ningún constructor, destructor u operador de asignación de copia definido por el usuario; ningún miembro de datos no estáticos privado o protegido; ningún miembro de datos no estáticos de tipo de referencia; ninguna clase base; ninguna función virtual ni ningún miembro de datos que tampoco cumpla estos requisitos. (Esto es esencialmente la definición de un tipo POD de C++03. Como la definición ha cambiado en el estándar C++11, no se recomienda usar `std::is_pod` para esta prueba). De lo contrario, el autor de la llamada asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como primer argumento. Los argumentos subsiguientes se desplazan entonces un argumento a la derecha. El destinatario debe devolver el mismo puntero en RAX.

Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:

### <a name="example-of-return-value-1---64-bit-result"></a>Ejemplo 1 de valor devuelto: resultado de 64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Ejemplo 2 de valor devuelto: resultado de 128 bits

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Ejemplo 3 de valor devuelto: resultado de tipo de usuario por puntero

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Ejemplo 4 de valor devuelto: resultado de tipo de usuario por valor

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registros guardados del autor y el destinatario de la llamada

Los registros RAX, RCX, RDX, R8, R9, R10, R11 y XMM0-5, y las partes superiores de YMM0-15 y ZMM0-15 se consideran volátiles y se deben considerar destruidos en llamadas de función (a menos que sean seguros y que esta seguridad se pueda demostrar mediante análisis, como la optimización de todo el programa). En AVX512VL, los registros del 16 al 31 de ZMM, YMM y XMM son volátiles.

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 y XMM6-15 se consideran no volátiles y una función que los use los debe guardar y restaurar.

## <a name="function-pointers"></a>Punteros de función

Los punteros de función son simplemente punteros a la etiqueta de la función respectiva. No hay requisitos de tabla de contenido (TOC) para los punteros de función.

## <a name="floating-point-support-for-older-code"></a>Compatibilidad del código antiguo con puntos flotantes

Los registros de la pila de punto flotante y MMX (MM0-MM7/ST0-ST7) se conservan en los cambios de contexto. No hay ninguna convención de llamada explícita para estos registros. El uso de estos registros está estrictamente prohibido en el código del modo kernel.

## <a name="fpcsr"></a>FpCsr

El estado del registro también incluye la palabra de control de FPU x87. La convención de llamada dicta este registro para que sea no volátil.

El registro de palabra de control de FPU x87 se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registro\[bits] | Parámetro |
|-|-|
| FPCSR\[0:6] | Máscaras de excepción, todos los 1 (todas las excepciones enmascaradas) |
| FPCSR\[7] | Reservado: 0 |
| FPCSR\[8:9] | Control de precisión: 10B (precisión doble) |
| FPCSR\[10:11] | Control de redondeo: 0 (redondeo al valor más próximo) |
| FPCSR\[12] | Control de infinito: 0 (no utilizado) |

Un destinatario que modifique cualquiera de los campos en FPCSR debe restaurarlos antes de devolverlos al autor de la llamada. Además, un autor de llamada que haya modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar a un destinatario, a menos que el destinatario espere los valores modificados por contrato.

Existen dos excepciones a las reglas sobre la no volatilidad de las marcas de control:

1. En funciones en las que el propósito documentado de la función determinada sea modificar las marcas FpCsr no volátiles.

1. Cuando sea correcto de un modo demostrable que la infracción de estas reglas dé como resultado un programa que se comporta igual que un programa en el que estas reglas no se infringen, por ejemplo, a través del análisis de programas completos.

## <a name="mxcsr"></a>MxCsr

El estado del registro también incluye MxCsr. La convención de llamada divide este registro en una parte volátil y una parte no volátil. La parte volátil consta de seis marcas de estado, en MXCSR\[0:5], mientras que el resto del registro, MXCSR\[6:15], se considera no volátil.

La parte no volátil se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registro\[bits] | Parámetro |
|-|-|
| MXCSR\[6] | Los desnormalizados son ceros: 0 |
| MXCSR\[7:12] | Máscaras de excepción, todos los 1 (todas las excepciones enmascaradas) |
| MXCSR\[13:14] | Control de redondeo: 0 (redondeo al valor más próximo) |
| MXCSR\[15] | Vaciado en cero para desbordamiento enmascarado: 0 (desactivado) |

Un destinatario que modifique cualquiera de los campos no volátiles en MXCSR debe restaurarlos antes de devolverlos al autor de la llamada. Además, un autor de llamada que haya modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar a un destinatario, a menos que el destinatario espere los valores modificados por contrato.

Existen dos excepciones a las reglas sobre la no volatilidad de las marcas de control:

- En funciones en las que el propósito documentado de la función determinada sea modificar las marcas MxCsr no volátiles.

- Cuando sea correcto de un modo demostrable que la infracción de estas reglas dé como resultado un programa que se comporta igual que un programa en el que estas reglas no se infringen, por ejemplo, a través del análisis de programas completos.

No se pueden realizar suposiciones sobre el estado de la parte volátil de MXCSR en un límite de función, a menos que se indique específicamente en la documentación de una función.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Al incluir setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dan como resultado un desenredado que invoca a destructores y llamadas de `__finally`.  Esto difiere de x86, donde incluir setjmp.h da como resultado que no se invocan las cláusulas y destructores `__finally`.

Una llamada a `setjmp` conserva el puntero de pila actual, los registros no volátiles y los registros MxCsr.  Las llamadas a `longjmp` devuelven al sitio de llamada `setjmp` más reciente y restablecen el puntero de pila, los registros no volátiles y los registros MxCsr de nuevo al estado que conserva la llamada de `setjmp` más reciente.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)
