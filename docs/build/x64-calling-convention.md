---
title: Convención de llamadas x64
description: Detalles de la Convención de llamada predeterminada de ABI de x64.
ms.date: 12/17/2018
ms.assetid: 41ca3554-b2e3-4868-9a84-f1b46e6e21d9
ms.openlocfilehash: 2cad00ac7f2cb5fe086fa262a0f512330997391f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856890"
---
# <a name="x64-calling-convention"></a>Convención de llamadas x64

En esta sección se describen los procesos y convenciones estándar que usa una función (el llamador) para realizar llamadas en otra función (el destinatario) en código x64.

## <a name="calling-convention-defaults"></a>Valores predeterminados de Convención de llamada

La interfaz binaria de aplicación (ABI) x64 utiliza de forma predeterminada una Convención de llamada de llamada rápida de cuatro registros. Se asigna espacio en la pila de llamadas como un almacén de instantáneas para que los destinatarios puedan guardar esos registros. Hay una correspondencia de uno a uno estricta entre los argumentos de una llamada de función y los registros utilizados para esos argumentos. Cualquier argumento que no quepa en 8 bytes, o que no sea 1, 2, 4 u 8 bytes, debe pasarse por referencia. Un único argumento nunca se reparte entre varios registros. La pila de registro de x87 no se utiliza y puede ser utilizada por el destinatario de la llamada, pero se debe considerar volátil en todas las llamadas de función. Todas las operaciones de punto flotante se realizan mediante los 16 registros de XMM. Los argumentos de entero se pasan en los registros RCX, RDX, R8 y R9. Los argumentos de punto flotante se pasan en XMM0L, XMM1L, XMM2L y XMM3L. los argumentos de 16 bytes se pasan por referencia. El paso de parámetros se describe en detalle en [paso de parámetros](#parameter-passing). Además de estos registros, RAX, R10, R11, XMM4 y XMM5 se consideran volátiles. Los demás registros no son volátiles. El uso de registros se documenta en detalle en registro del [uso de registros](../build/x64-software-conventions.md#register-usage) y [registros guardados del destinatario](#callercallee-saved-registers).

En el caso de las funciones prototipos, todos los argumentos se convierten en los tipos de destinatarios esperados antes de pasar. El autor de la llamada es responsable de asignar espacio para los parámetros al destinatario y siempre debe asignar espacio suficiente para almacenar cuatro parámetros de registro, incluso si el destinatario no toma ese número de parámetros. Esta Convención simplifica la compatibilidad con las funciones de lenguaje C no prototipo y las funciones varargC++ de t/. En el caso de las funciones vararg o sin prototipo, los valores de punto flotante se deben duplicar en el registro de uso general correspondiente. Cualquier parámetro más allá de los cuatro primeros se debe almacenar en la pila después del almacén de instantáneas antes de la llamada. Los detalles de la función vararg se pueden encontrar en [varargs](#varargs). La información de funciones no prototipos se detalla en [funciones no prototipos](#unprototyped-functions).

## <a name="alignment"></a>Alignment

La mayoría de las estructuras se alinean con su alineación natural. Las excepciones principales son el puntero de pila y `malloc` o la memoria `alloca`, que se alinean con 16 bytes para ayudar al rendimiento. La alineación por encima de 16 bytes se debe realizar manualmente, pero como 16 bytes es un tamaño de alineación común para las operaciones XMM, este valor debería funcionar para la mayoría del código. Para obtener más información sobre la alineación y el diseño de la estructura, consulte [tipos y almacenamiento](../build/x64-software-conventions.md#types-and-storage). Para obtener información sobre el diseño de la pila, vea uso de la [pila de x64](../build/stack-usage.md).

## <a name="unwindability"></a>Desenredo

Las funciones de hoja son funciones que no cambian ningún registro no volátil. Una función no hoja puede cambiar RSP no volátil, por ejemplo, llamando a una función o asignando espacio de pila adicional para las variables locales. Para recuperar registros no volátiles cuando se controla una excepción, las funciones no hoja se deben anotar con datos estáticos que describen cómo desenredar correctamente la función en una instrucción arbitraria. Estos datos se almacenan como *pdata*, o datos de procedimientos, que a su vez hacen referencia a *XData*, los datos de control de excepciones. XData contiene la información de desenredo y puede apuntar a un pdata adicional o a una función de controlador de excepciones. Los registros y los problemas de registro están muy restringidos para que se puedan describir correctamente en XData. El puntero de pila debe estar alineado a 16 bytes en cualquier región de código que no forme parte de un epílogo o prólogo, excepto en las funciones de hoja. Las funciones de hoja se pueden desenredar simplemente simulando una devolución, por lo que no se requiere pdata ni XData. Para obtener más información sobre la estructura adecuada de los registros de función y los [epílogos](../build/prolog-and-epilog.md), vea el prólogo y el epílogo de x64. Para obtener más información sobre el control de excepciones y el control de excepciones y el desenredo de pdata y Xdata, vea [control de excepciones x64](../build/exception-handling-x64.md).

## <a name="parameter-passing"></a>Paso de parámetros

Los cuatro primeros argumentos de tipo entero se pasan en registros. Los valores enteros se pasan en orden de izquierda a derecha en RCX, RDX, R8 y R9, respectivamente. Los argumentos cinco y superiores se pasan en la pila. Todos los argumentos están justificados a la derecha en registros, por lo que el destinatario puede pasar por alto los bits superiores del registro y tener acceso solo a la parte del registro necesaria.

Los argumentos de punto flotante y precisión doble de los cuatro primeros parámetros se pasan en XMM0-XMM3, en función de la posición. El entero registra RCX, RDX, R8 y R9 que normalmente se utilizarían para esas posiciones se omiten, excepto en el caso de argumentos varargs. Para obtener más información, vea [varargs](#varargs). Del mismo modo, los registros de XMM0-XMM3 se omiten cuando el argumento correspondiente es un tipo entero o de puntero.

los tipos de [__m128](../cpp/m128.md) , las matrices y las cadenas nunca se pasan por valor inmediato. En su lugar, se pasa un puntero a la memoria asignada por el llamador. Los Structs y las uniones de los tipos de tamaño 8, 16, 32, 64 y __m64, se pasan como si fueran enteros del mismo tamaño. Los Structs o uniones de otros tamaños se pasan como un puntero a la memoria asignada por el llamador. Para estos tipos de agregado pasados como puntero, incluido \__m128, la memoria temporal asignada por el llamador debe tener una alineación de 16 bytes.

Las funciones intrínsecas que no asignan espacio de pila y no llaman a otras funciones, a veces usan otros registros volátiles para pasar argumentos de registro adicionales. Esta optimización se realiza mediante el estricto enlace entre el compilador y la implementación de función intrínseca.

El destinatario es responsable de volcar los parámetros de registro en su espacio de sombra si es necesario.

En la tabla siguiente se resume cómo se pasan los parámetros:

|Tipo de parámetro|Cómo se pasan|
|--------------------|----------------|
|Punto flotante|Primeros 4 parámetros: XMM0 a XMM3. Otras pasadas en la pila.|
|Entero|Primeros 4 parámetros: RCX, RDX, R8, R9. Otras pasadas en la pila.|
|Agregados (8, 16, 32 o 64 bits) y __m64|Primeros 4 parámetros: RCX, RDX, R8, R9. Otras pasadas en la pila.|
|Agregados (otros)|Por puntero. Primeros 4 parámetros pasados como punteros en RCX, RDX, R8 y R9|
|__m128|Por puntero. Primeros 4 parámetros pasados como punteros en RCX, RDX, R8 y R9|

### <a name="example-of-argument-passing-1---all-integers"></a>Ejemplo de paso de argumentos 1: todos los enteros

```cpp
func1(int a, int b, int c, int d, int e);
// a in RCX, b in RDX, c in R8, d in R9, e pushed on stack
```

### <a name="example-of-argument-passing-2---all-floats"></a>Ejemplo de paso de argumento 2-todos los flotantes

```cpp
func2(float a, double b, float c, double d, float e);
// a in XMM0, b in XMM1, c in XMM2, d in XMM3, e pushed on stack
```

### <a name="example-of-argument-passing-3---mixed-ints-and-floats"></a>Ejemplo de paso de argumento 3: enteros combinados y flotantes

```cpp
func3(int a, double b, int c, float d);
// a in RCX, b in XMM1, c in R8, d in XMM3
```

### <a name="example-of-argument-passing-4--__m64-__m128-and-aggregates"></a>Ejemplo de paso de argumento 4-__m64, \__m128 y agregados

```cpp
func4(__m64 a, _m128 b, struct c, float d);
// a in RCX, ptr to b in RDX, ptr to c in R8, d in XMM3
```

## <a name="varargs"></a>Varargs

Si los parámetros se pasan a través de varargs (por ejemplo, argumentos de puntos suspensivos), se aplica la Convención normal de paso de los parámetros de registro, incluyendo el desbloqueo del quinto y los argumentos subsiguientes a la pila. Es responsabilidad del destinatario de volcar los argumentos que tienen su dirección tomada. Solo para los valores de punto flotante, tanto el registro entero como el registro de punto flotante deben contener el valor, en caso de que el destinatario espere el valor de los registros enteros.

## <a name="unprototyped-functions"></a>Funciones no prototipo

En el caso de las funciones que no tienen un prototipo completo, el llamador pasa valores enteros como enteros y valores de punto flotante como precisión doble. Solo para los valores de punto flotante, tanto el registro entero como el registro de punto flotante contienen el valor Float en caso de que el destinatario espere el valor de los registros enteros.

```cpp
func1();
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7
   func1(2, 1.0, 7);
}
```

## <a name="return-values"></a>Valores devueltos

Un valor devuelto escalar que puede caber en 64 bits se devuelve a través de RAX; Esto incluye tipos de __m64. En XMM0 se devuelven tipos no escalares, incluidos los tipos Float, Double y Vector, como [__m128](../cpp/m128.md), [__m128i](../cpp/m128i.md) [__m128d](../cpp/m128d.md) . El estado de bits no usados en el valor devuelto en RAX o XMM0 es indefinido.

Se pueden devolver tipos definidos por el usuario por valor de funciones globales y funciones miembro estáticas. Para devolver un tipo definido por el usuario por valor en RAX, debe tener una longitud de 1, 2, 4, 8, 16, 32 o 64 bits. También debe tener un constructor definido por el usuario, un destructor o un operador de asignación de copia; ningún miembro de datos no estático privado o protegido; no hay miembros de datos no estáticos del tipo de referencia; ninguna clase base; no hay funciones virtuales; y ningún miembro de datos que no cumpla también estos requisitos. (Esto es esencialmente la definición de un tipo POD de C++03. Dado que la definición ha cambiado en el estándar de C++ 11, no se recomienda usar `std::is_pod` para esta prueba). De lo contrario, el llamador asume la responsabilidad de asignar memoria y pasar un puntero para el valor devuelto como primer argumento. Los argumentos subsiguientes se desplazan entonces un argumento a la derecha. El destinatario debe devolver el mismo puntero en RAX.

Estos ejemplos muestran cómo se pasan los parámetros y valores devueltos para las funciones con las declaraciones especificadas:

### <a name="example-of-return-value-1---64-bit-result"></a>Ejemplo de resultado de valor devuelto de 1-64 bits

```Output
__int64 func1(int a, float b, int c, int d, int e);
// Caller passes a in RCX, b in XMM1, c in R8, d in R9, e pushed on stack,
// callee returns __int64 result in RAX.
```

### <a name="example-of-return-value-2---128-bit-result"></a>Ejemplo de resultado de valor devuelto de 2-128 bits

```Output
__m128 func2(float a, double b, int c, __m64 d);
// Caller passes a in XMM0, b in XMM1, c in R8, d in R9,
// callee returns __m128 result in XMM0.
```

### <a name="example-of-return-value-3---user-type-result-by-pointer"></a>Ejemplo de valor devuelto 3-tipo de usuario resultado por puntero

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

## <a name="callercallee-saved-registers"></a>Registros guardados del llamador y del destinatario

Los registros RAX, RCX, RDX, R8, R9, R10, R11, XMM0-5 y las partes superiores de YMM0-15 y ZMM0-15 se consideran volátiles y se deben considerar destruidos en llamadas a funciones (a menos que la seguridad opuestas por el análisis, como la optimización de todo el programa). En AVX512VL, los registros ZMM, YMM y XMM 16-31 son volátiles.

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14, R15 y XMM6-15 se consideran no volátiles y se deben guardar y restaurar mediante una función que los use.

## <a name="function-pointers"></a>Punteros de función
 
Los punteros de función son simplemente punteros a la etiqueta de la función respectiva. No hay requisitos de tabla de contenido (TOC) para los punteros de función.

## <a name="floating-point-support-for-older-code"></a>Compatibilidad de punto flotante con código anterior

Los registros de la pila de punto flotante y MMX (MM0-MM7/ST0-ST7) se conservan en los cambios de contexto. No hay ninguna Convención de llamada explícita para estos registros. El uso de estos registros está estrictamente prohibido en el código del modo kernel.

## <a name="fpcsr"></a>FpCsr

El estado del registro también incluye la palabra de control FPU x87. La Convención de llamada dicta este registro para que no sea volátil.

El registro de palabras de control FPU x87 se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registro de\[bits] | Configuración |
|-|-|
| FPCSR\[0:6] | Máscaras de excepción todas 1 (todas las excepciones enmascaradas) |
| FPCSR\[7] | Reservado-0 |
| FPCSR\[8:9] | Control de precisión-10B (precisión doble) |
| FPCSR\[10:11] | Control de redondeo-0 (redondeo al más próximo) |
| FPCSR\[12] | Control de infinito-0 (no se usa) |

Un destinatario que modifique cualquiera de los campos dentro de FPCSR debe restaurarlos antes de volver a su llamador. Además, un llamador que haya modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar a un destinatario de la llamada a menos que el destinatario espere los valores modificados.

Existen dos excepciones a las reglas sobre la no volatilidad de las marcas de control:

1. En las funciones en las que el propósito documentado de la función determinada es modificar las marcas FpCsr no volátiles.

1. Cuando es provably corregir que la infracción de estas reglas da como resultado un programa que se comporta igual que un programa en el que estas reglas no se infringen, por ejemplo, a través del análisis de programas completos.

## <a name="mxcsr"></a>MxCsr

El estado del registro también incluye MxCsr. La Convención de llamada divide este registro en una parte volátil y una parte no volátil. La parte volátil consta de seis marcas de estado, en MXCSR\[0:5], mientras que el resto del registro, MXCSR\[6:15], se considera no volátil.

La parte no volátil se establece en los siguientes valores estándar al inicio de la ejecución del programa:

| Registro de\[bits] | Configuración |
|-|-|
| MXCSR\[6] | Las desnormalizaciones son ceros-0 |
| MXCSR\[7:12] | Máscaras de excepción todas 1 (todas las excepciones enmascaradas) |
| MXCSR\[13:14] | Control de redondeo-0 (redondeo al más próximo) |
| MXCSR\[15] | Vaciar en cero para subdesbordamiento enmascarado-0 (desactivado) |

Un destinatario que modifique cualquiera de los campos no volátiles dentro de MXCSR debe restaurarlos antes de volver a su llamador. Además, un llamador que haya modificado cualquiera de estos campos debe restaurarlos a sus valores estándar antes de invocar a un destinatario de la llamada a menos que el destinatario espere los valores modificados.

Existen dos excepciones a las reglas sobre la no volatilidad de las marcas de control:

- En las funciones en las que el propósito documentado de la función determinada es modificar las marcas MxCsr no volátiles.

- Cuando es provably corregir que la infracción de estas reglas da como resultado un programa que se comporta igual que un programa en el que estas reglas no se infringen, por ejemplo, a través del análisis de programas completos.

No se pueden realizar suposiciones sobre el estado de la parte volátil de MXCSR a través de un límite de función, a menos que se indique específicamente en la documentación de una función.

## <a name="setjmplongjmp"></a>setjmp/longjmp

Al incluir setjmpex. h o setjmp. h, todas las llamadas a [setjmp](../c-runtime-library/reference/setjmp.md) o [longjmp](../c-runtime-library/reference/longjmp.md) dan como resultado un desenredado que invoca a destructores y llamadas `__finally`.  Esto difiere de x86, donde incluir setjmp. h da como resultado la invocación de `__finally` cláusulas y destructores.

Una llamada a `setjmp` conserva el puntero de pila actual, los registros no volátiles y los registros MxCsr.  Las llamadas a `longjmp` volver al sitio de llamada `setjmp` más reciente y restablece el puntero de pila, los registros no volátiles y los registros MxCsr, de nuevo al estado conservado por la llamada de `setjmp` más reciente.

## <a name="see-also"></a>Consulte también

[Convenciones de software x64](../build/x64-software-conventions.md)
