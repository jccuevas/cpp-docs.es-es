---
title: Convención de llamadas x64
description: Detalles de la convención de llamada predeterminada x64 ABI.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 0e3da5cea44437c132b5c2ea522bd229ea000a10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2019
ms.locfileid: "67861157"
---
# <a name="x64-calling-convention"></a>Convención de llamadas x64

Esta sección describen los procesos estándar y convenciones que usa una función (el llamador) para realizar llamadas a otra función (el destinatario) en x64 código.

## <a name="calling-convention-defaults"></a>Valores predeterminados de convención de llamada

De forma predeterminada el x64 interfaz binaria de aplicación (ABI) usa una registro de cuatro fast convención de llamada por. Se asigna espacio en la pila de llamadas como almacén de instantáneas de destinatarios guardar esos registros. Hay una correspondencia estricta entre los argumentos de una llamada de función y los registros que se usan para los argumentos. Cualquier argumento que no cabe en 8 bytes o no es 1, 2, 4 u 8 bytes, se debe pasar por referencia. Un único argumento nunca se reparte entre varios registros. X87 registrar la pila no está en uso y se puede usar el destinatario, pero debe considerarse volátil en las llamadas de función. Punto flotante de todas las operaciones se realizan utilizando los 16 registros de XMM. Argumentos de entero se pasan en registros RCX, RDX, R8 y R9. Los argumentos se pasan en XMM0L, XMM1L, XMM2L y XMM3L de punto flotante. argumentos de 16 bytes se pasan por referencia. Paso de parámetros se describen en detalle en [pasando el parámetro](#parameter-passing). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. Todos los demás registros son volátiles. Uso de registros se documenta detalladamente en [registrar uso](../build/x64-software-conventions.md#register-usage) y [guardado registra el llamador y destinatario](#callercallee-saved-registers).

Las funciones prototipo, todos los argumentos se convierten a los tipos de destinatario esperado antes de pasar. El llamador es responsable de asignar espacio para los parámetros para el destinatario y siempre debe asignar espacio suficiente para almacenar los cuatro parámetros de registro, incluso si el destinatario no toma parámetros esa cantidad. Esta convención simplifica la compatibilidad con funciones de lenguaje C sin prototipo y funciones de C o C++ vararg. Para funciones vararg o sin prototipo, cualquier punto flotante, los valores deben duplicarse en el registro de uso general correspondiente. Los parámetros más allá de los primeros cuatro se deben almacenar en la pila después de almacenar las instantáneas antes de la llamada. Detalles de la función vararg pueden encontrarse en [Varargs](#varargs). Información de la función sin prototipo se detalla en [funciones sin prototipo](#unprototyped-functions).

## <a name="alignment"></a>Alineación

Mayoría de las estructuras se alinea según su alineación natural. Las excepciones principales son el puntero de pila y `malloc` o `alloca` memoria, lo que se alinean a 16 bytes para ayudar al rendimiento. La alineación por encima de 16 bytes que debe realizarse manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones de registros de XMM, este valor debería funcionar para la mayoría del código. Para obtener más información sobre el diseño de la estructura y la alineación, vea [tipos y almacenamiento](../build/x64-software-conventions.md#types-and-storage). Para obtener información sobre el diseño de pila, vea [x64 de uso de la pila](../build/stack-usage.md).

## <a name="unwindability"></a>Capacidad de desenredar

Las funciones de hoja son funciones que no cambian los registros no volátiles. Una función no hoja puede cambiar RSP no volátil, por ejemplo, llamando a una función o asignación de espacio de pila adicional para las variables locales. Con el fin de recuperar los registros no volátiles cuando se controla una excepción, las funciones de hoja no se deben anotar con datos estáticos que se describen cómo la función en una instrucción arbitraria de desenredado correctamente. Estos datos se almacenan como *pdata*, o datos de procedimiento, que a su vez hace referencia a *xdata*, los datos de control de excepciones. Contiene la información de desenredo lo xdata y puede apuntar a pdata adicional o una función de controlador de excepción. Los prólogos y epílogos están muy restringida para que se pueden describir correctamente en xdata. El puntero de pila se alineen con 16 bytes en cualquier región de código que no forma parte de un epílogo ni un prólogo, excepto dentro de las funciones de hoja. Las funciones de hoja se pueden desenredas simplemente simulando una devolución, por lo que no se requieren pdata y xdata. Para obtener más información acerca de la estructura adecuada de la función prólogos y epílogos, consulte [x64 prólogo y epílogo](../build/prolog-and-epilog.md). Para obtener más información sobre el control de excepciones y el control de excepciones y desenredo de pdata y xdata, vea [x64 control de excepciones](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Paso de parámetros

Los primeros cuatro argumentos de entero se pasan en registros. Los valores enteros se pasan en orden de izquierda a derecha en RCX, RDX, R8 y R9, respectivamente. Cinco argumentos y superior se pasan en la pila. Todos los argumentos son justificado a la derecha en los registros, por lo que el destinatario puede omitir los bits superiores del registro y tener acceso a solo la parte del registro necesaria.

Los argumentos de punto flotante y doble precisión en los cuatro primeros parámetros se pasan en XMM0: XMM3, dependiendo de la posición. Los registros de enteros RCX, RDX, R8 y R9 que se usan normalmente para las posiciones se omiten, salvo en el caso de argumentos de varargs. Para obtener más información, consulte [Varargs](#varargs). De forma similar, el XMM0: XMM3 registros se omiten cuando el argumento correspondiente es un tipo entero o puntero.

[__m128](../cpp/m128.md) cadenas, matrices y tipos nunca se pasan por valor inmediato. En su lugar, se pasa un puntero a la memoria asignada por el llamador. Estructuras y uniones de tamaño 8, 16, 32 o 64 bits y tipos __m64, se pasan como si fueran enteros del mismo tamaño. Structs o uniones de otros tamaños se pasan como un puntero a la memoria asignada por el llamador. Para estos tipos de agregado se pasa como un puntero, incluidos \__m128, la memoria temporal asignada por el llamador debe ser la alineación de 16 bytes.

Funciones intrínsecas que no asignación espacio de pila y no llaman a otras funciones, en ocasiones, usan otros registros variables para pasar argumentos de registro adicionales. Esta optimización se realiza mediante la estrecha relación entre el compilador y la implementación de la función intrínseca.

El destinatario es responsable de volcar los parámetros de registro en su espacio de sombra si es necesario.

En la tabla siguiente se resume cómo se pasan los parámetros:

|Tipo de parámetro|Cómo se pasa|
|--------------------|----------------|
|Punto flotante|4 primeros parámetros - XMM0 a XMM3. Otros se pasan en la pila.|
|Entero|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|
|Agregados (8, 16, 32 o 64 bits) y __m64|4 primeros parámetros - RCX, RDX, R8, R9. Otros se pasan en la pila.|
|Agregados (otros)|Por el puntero. En primer lugar 4 parámetros se pasan como punteros en RCX, RDX, R8 y R9|
|__m128|Por el puntero. En primer lugar 4 parámetros se pasan como punteros en RCX, RDX, R8 y R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo del paso 1: todos los enteros de argumentos

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo del paso 2: todos los valores de punto flotante de argumentos

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo del paso 3: enteros y flotantes combinados de argumentos

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--m64-m128-and-aggregates"></a>Ejemplo del paso 4 de argumentos-__m64, \__m128 y agregados

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, los argumentos de puntos suspensivos), a continuación, aplica el parámetro de registro normal pasando la convención, incluyendo los argumentos de la quinto y posteriores a la pila. Es responsabilidad del destinatario para volcar los argumentos ceder su dirección. Para valores de punto flotante, el registro entero y el registro de punto flotante deben contener el valor, en caso de que el destinatario espere el valor de los registros enteros.

## <a name="unprototyped-functions"></a>Funciones sin prototipo

Para las funciones no ajusten completamente al prototipo, el llamador pasa valores enteros como enteros y valores de punto flotante como de doble precisión. Para valores de punto flotante, el registro entero y el registro de punto flotante contienen el valor de punto flotante en caso de que el destinatario espere el valor de los registros enteros.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valores devueltos

Un valor escalar devuelto que puede caber en 64 bits se devuelve mediante RAX; Esto incluye tipos __m64. Los tipos no escalares como flotantes, dobles y tipos de vector como [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md), [__m128d](../cpp/m128d.md) se devuelven en XMM0. El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.

Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas. Para devolver un tipo definido por el usuario por valor en RAX, debe tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits. También no debe tener ningún constructor definido por el usuario, un destructor o un operador de asignación de copia. ningún miembro de datos no estático privado o protegido; ningún miembro de datos no estáticos del tipo de referencia; No hay clases bases; ninguna función virtual; y ningún miembro de datos que no cumple estos requisitos también. (Esto es esencialmente la definición de un tipo POD de C++03. Dado que ha cambiado la definición en el estándar C ++ 11, no se recomienda usar `std::is_pod` para esta prueba.) De lo contrario, el llamador asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como primer argumento. Los argumentos subsiguientes se desplazan entonces un argumento a la derecha. El destinatario debe devolver el mismo puntero en RAX.

Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:

### <a name="example-of-return-value-1---64-bit-result"></a>Ejemplo de valor devuelto de 1: resultado de 64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Ejemplo 2: resultado de 128 bits de valor devuelto de

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Ejemplo de valor devuelto 3: resultado de tipo de usuario por puntero

```Output
struct Struct1 {
   int j, k, l;    // Struct1 exceeds 64 bits.
};
Struct1 func3(int a, double b, int c, float d);
// Caller allocates memory for Struct1 returned and passes pointer in RCX,
// a in RDX, b in XMM2, c in R9, d pushed on the stack;
// callee returns pointer to Struct1 result in RAX.
```

### <a name="example-of-return-value-4---user-type-result-by-value"></a>Ejemplo de valor devuelto 4: resultado de tipo de usuario por valor

```Output
struct Struct2 {
   int j, k;    // Struct2 fits in 64 bits, and meets requirements for return by value.
};
Struct2 func4(int a, double b, int c, float d);
// Caller passes a in RCX, b in XMM1, c in R8, and d in XMM3;
// callee returns Struct2 result by value in RAX.
```

## <a name="callercallee-saved-registers"></a>Registros guardado del llamador y destinatario

Destruyen los registros RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 y las partes superiores de YMM0-15 y ZMM0-15 se consideran volátil y se deben considerar en las llamadas de función (a menos que en caso contrario, seguridad-opuestas por análisis como la optimización de todo el programa). En AVX512VL, los registros XMM, YMM y ZMM 16-31 son volátiles.

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 y XMM6-15 se consideran no volátiles y deben guardarse y restaurarse con una función que los usa.

## <a name="function-pointers"></a>Punteros de función
 
Punteros de función son simplemente punteros a la etiqueta de la función respectiva. No hay ninguna tabla de requisitos de contenido (TDC) para punteros de función.

## <a name="floating-point-support-for-older-code"></a>Compatibilidad de punto flotante código antiguo

Los registros MMX y pila de punto flotante (MM0 MM7/ST0 ST7) se conservan a través de los cambios de contexto. No hay ninguna convención de llamada explícita para estos registros. El uso de estos registros está prohibido en el código de modo kernel.

## <a name="fpcsr"></a>FpCsr

El estado del registro también incluye x87 palabra de control FPU. La convención de llamada dicta el registro para que sea permanente.

X87 registro de palabra de control FPU se establece en los valores estándar siguientes al principio de la ejecución del programa:

| Registrar\[bits] | Parámetro |
|-|-|
| FPCSR\[0:6] | Excepción enmascara todos los valores 1 (se enmascaran todas las excepciones) |
| FPCSR\[7] | Reservado - 0 |
| FPCSR\[8:9] | Control de precisión - 10B (precisión doble) |
| FPCSR\[10:11] | Control de redondeo: 0 (redondeo al más cercano) |
| FPCSR\[12] | Control de infinito: 0 (no utilizado) |

Un destinatario que modifica cualquiera de los campos dentro de FPCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que se ha modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario a menos que el contrato, el destinatario espere los valores modificados.

Hay dos excepciones a las reglas sobre no volátiles de las marcas de control:

1. En funciones donde es el propósito documentado de la función especificada modificar el control FPCSR no volátiles marcas.

1. Cuando es probablemente una correcta que da como resultado la infracción de estas reglas en un programa que se comporta igual que un programa donde no se infringen estas reglas, por ejemplo, mediante el análisis de todo el programa.

## <a name="mxcsr"></a>MxCsr

El estado del registro también incluye MxCsr. La convención de llamada divide este registro en una parte volátil y una parte permanente. La parte variable consta de las marcas de estado de seis en MXCSR\[0:5], mientras que el resto del registro, MXCSR\[6:15], se considera no volátil.

La parte no variable se establece en los valores estándar siguientes al principio de la ejecución del programa:

| Registrar\[bits] | Parámetro |
|-|-|
| MXCSR\[6] | Denormals son ceros - 0 |
| MXCSR\[7:12] | Excepción enmascara todos los valores 1 (se enmascaran todas las excepciones) |
| MXCSR\[13:14] | Control de redondeo: 0 (redondeo al más cercano) |
| MXCSR\[15] | Vaciar en cero subdesbordamiento enmascarado - 0 (desactivado) |

Un destinatario que modifica cualquiera de los campos no volátiles dentro de MXCSR debe restaurarlos antes de devolver al llamador. Además, un llamador que se ha modificado alguno de estos campos debe restaurarlos a sus valores estándares antes de invocar a un destinatario a menos que el contrato, el destinatario espere los valores modificados.

Hay dos excepciones a las reglas sobre no volátiles de las marcas de control:

- En funciones donde es el propósito documentado de la función especificada modificar el registro de MxCsr no volátil marcas.

- Cuando es probablemente una correcta que da como resultado la infracción de estas reglas en un programa que se comporta igual que un programa donde no se infringen estas reglas, por ejemplo, mediante el análisis de todo el programa.

Se pueden hacer ninguna suposición sobre el estado de la parte variable de MXCSR a través de un límite de función, a menos que se describen específicamente en la documentación de la función.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Al incluir setjmpex.h o setjmp.h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dar lugar a una operación de desenredo que invoca destructores y `__finally` llamadas.  Esto difiere de x86, donde produce setjmp.h incluidos `__finally` cláusulas y destructores no que se va a invocar.

Una llamada a `setjmp` conserva el puntero de pila actual, registros no volátiles y registros de MxCsr.  Las llamadas a `longjmp` vuelva a la más reciente `setjmp` llamar al sitio y restablece el puntero de pila y registros no volátiles MxCsr registra, vuelve al estado mantenido desde la última `setjmp` llamar.

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)
