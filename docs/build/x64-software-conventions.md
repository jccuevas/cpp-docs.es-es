---
title: Convenciones de software x64
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422725"
---
# <a name="x64-software-conventions"></a>Convenciones de software x64

En esta sección se describe la metodología de convención de llamada de C++ para x64, la extensión de 64 bits de la arquitectura x86.

## <a name="overview-of-x64-calling-conventions"></a>Información general sobre las convenciones de llamada de x64

Dos diferencias importantes entre x86 y x64 son la capacidad de direccionamiento de 64 bits y un conjunto plano de 16 registros de 64 bits para uso general. Dado el conjunto de registros expandido, x64 usa la convención de llamada [__fastcall](../cpp/fastcall.md) y un modelo de control de excepciones basado en RISC. La convención `__fastcall` usa registros para los primeros cuatro argumentos y el marco de pila para pasar argumentos adicionales. Para obtener información detallada sobre la convención de llamada de x64, incluido el uso de registros, parámetros de la pila, valores devueltos y el desenredado de la pila, vea [Convención de llamada de x64](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Habilitación de la optimización para x64

La siguiente opción del compilador le ayuda a optimizar la aplicación para x64:

- [/favor (Optimizar para valores específicos de la arquitectura)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Tipos y almacenamiento

En esta sección se describe la enumeración y el almacenamiento de tipos de datos para la arquitectura x64.

### <a name="scalar-types"></a>Tipos escalares

Aunque es posible acceder a los datos con cualquier alineación, se recomienda alinearlos en su límite natural, o por algún múltiplo, para evitar la pérdida de rendimiento. Las enumeraciones son enteros constantes y se tratan como enteros de 32 bits. En la tabla siguiente se describe la definición de tipo y el almacenamiento recomendado para los datos con relación a la alineación mediante los valores de alineación siguientes:

- Byte: 8 bits

- Palabra: 16 bits

- Doble palabra: 32 bits

- Palabra cuádruple: 64 bits

- Doble palabra cuádruple: 128 bits

|||||
|-|-|-|-|
|Tipo escalar|Tipo de datos de C|Tamaño de almacenamiento (en bytes)|Alineación recomendada|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Palabra|
|**UINT16**|**unsigned short**|2|Palabra|
|**INT32**|**int**, **long**|4|Doble palabra|
|**UINT32**|**unsigned int, unsigned long**|4|Doble palabra|
|**INT64**|**__int64**|8|Palabra cuádruple|
|**UINT64**|**unsigned __int64**|8|Palabra cuádruple|
|**FP32 (precisión sencilla)**|**float**|4|Doble palabra|
|**FP64 (precisión doble)**|**double**|8|Palabra cuádruple|
|**POINTER**|__\*__|8|Palabra cuádruple|
|**__m64**|**estructura __m64**|8|Palabra cuádruple|
|**__m128**|**estructura __m128**|16|Doble palabra cuádruple|

### <a name="aggregates-and-unions"></a>Agregados y uniones

Otros tipos, como las matrices, estructuras y uniones, tienen requisitos de alineación más estrictos que garantizan el almacenamiento y la recuperación de datos coherentes de los agregados y las uniones. Estas son las definiciones de matriz, estructura y unión:

- Matriz

   Contiene un grupo ordenado de objetos de datos adyacentes. Cada objeto se denomina *elemento*. Todos los elementos de una matriz tienen el mismo tamaño y tipo de datos.

- Estructura

   Contiene un grupo ordenado de objetos de datos. A diferencia de los elementos de una matriz, los objetos de datos de una estructura pueden tener distintos tamaños y tipos de datos. Cada objeto de datos de una estructura se denomina *miembro*.

- Unión

   Objeto que contiene cualquiera de un conjunto de miembros con nombre. Los miembros del conjunto con nombre pueden ser de cualquier tipo. El almacenamiento asignado para una unión es igual al almacenamiento necesario para el miembro más grande de esa unión, además de cualquier relleno necesario para la alineación.

En la tabla siguiente se muestra la alineación recomendada para los miembros escalares de uniones y estructuras.

||||
|-|-|-|
|Tipo escalar|Tipo de datos de C|Alineación necesaria|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Palabra|
|**UINT16**|**unsigned short**|Palabra|
|**INT32**|**int**, **long**|Doble palabra|
|**UINT32**|**unsigned int, unsigned long**|Doble palabra|
|**INT64**|**__int64**|Palabra cuádruple|
|**UINT64**|**unsigned __int64**|Palabra cuádruple|
|**FP32 (precisión sencilla)**|**float**|Doble palabra|
|**FP64 (precisión doble)**|**double**|Palabra cuádruple|
|**POINTER**|<strong>\*</strong>|Palabra cuádruple|
|**__m64**|**estructura __m64**|Palabra cuádruple|
|**__m128**|**estructura __m128**|Doble palabra cuádruple|

Se aplican las siguientes reglas de alineación de agregados:

- La alineación de una matriz es la misma que la alineación de uno de los elementos de la matriz.

- La alineación del inicio de una estructura o una unión es la alineación máxima de cualquier miembro individual. Cada miembro de la estructura o unión se debe colocar en su alineación adecuada, como se ha definido en la tabla anterior, lo que puede requerir un relleno interno implícito, en función del miembro anterior.

- El tamaño de la estructura debe ser un múltiplo entero de su alineación, lo que puede requerir relleno después del último miembro. Como las estructuras y las uniones se pueden agrupar en matrices, cada elemento de matriz de una estructura o unión debe comenzar y finalizar en la alineación adecuada determinada antes.

- Es posible alinear los datos de tal forma que sean mayores que los requisitos de alineación, siempre y cuando se mantengan las reglas anteriores.

- Un compilador individual puede ajustar el empaquetado de una estructura por motivos de tamaño. Por ejemplo, [/Zp (alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.

### <a name="examples-of-structure-alignment"></a>Ejemplos de alineación de estructuras

En los cuatro ejemplos siguientes se declara una estructura alineada o una unión, y en las figuras correspondientes se muestra el diseño de esa estructura o unión en la memoria. Cada columna de una ilustración representa un byte de memoria, y el número de la columna indica el desplazamiento de ese byte. El nombre de la segunda fila de cada ilustración se corresponde con el nombre de una variable en la declaración. Las columnas sombreadas indican el relleno necesario para lograr la alineación especificada.

#### <a name="example-1"></a>Ejemplo 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Diseño de la estructura del ejemplo 1 de conversión de AMD](../build/media/vcamd_conv_ex_1_block.png "Diseño de la estructura del ejemplo 1 de conversión de AMD")

#### <a name="example-2"></a>Ejemplo 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Diseño de la estructura del ejemplo 2 de conversión de AMD](../build/media/vcamd_conv_ex_2_block.png "Diseño de la estructura del ejemplo 2 de conversión de AMD")

#### <a name="example-3"></a>Ejemplo 3

```C
// Total size = 12 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Diseño de la estructura del ejemplo 3 de conversión de AMD](../build/media/vcamd_conv_ex_3_block.png "Diseño de la estructura del ejemplo 3 de conversión de AMD")

#### <a name="example-4"></a>Ejemplo 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Diseño de la estructura del ejemplo 4 de conversión de AMD](../build/media/vcamd_conv_ex_4_block.png "Diseño de la estructura del ejemplo 4 de conversión de AMD")

### <a name="bitfields"></a>Campos de bits

Los campos de bits de estructura se limitan a 64 bits y pueden ser de tipo signed int, unsigned int, int64 o unsigned int64. Los campos de bits que cruzan el límite de tipos omiten bits para alinear el campo de bits con la alineación de tipos siguiente. Por ejemplo, los campos de bits enteros no pueden cruzar un límite de 32 bits.

### <a name="conflicts-with-the-x86-compiler"></a>Conflictos con el compilador de x86

Los tipos de datos de más de 4 bytes no se alinean automáticamente en la pila cuando se usa el compilador de x86 para compilar una aplicación. Como la arquitectura del compilador de x86 es una pila alineada de 4 bytes, todo lo que sea mayor de 4 bytes, por ejemplo, un entero de 64 bits, no se puede alinear de forma automática a una dirección de 8 bytes.

Trabajar con datos sin alinear tiene dos implicaciones.

- Se puede tardar más en acceder a ubicaciones no alineadas de lo que se tarda en acceder a ubicaciones alineadas.

- Las ubicaciones no alineadas no se pueden usar en operaciones de bloqueo.

Si necesita una alineación más estricta, use `__declspec(align(N))` en las declaraciones de variables. Esto hace que el compilador alinee de forma dinámica la pila para cumplir con las especificaciones. Pero el ajuste dinámico de la pila en tiempo de ejecución puede ralentizar la ejecución de la aplicación.

## <a name="register-usage"></a>Uso de registros

La arquitectura x64 proporciona 16 registros generales (que se denominarán registros enteros a partir de ahora), así como otros 16 registros de XMM/YMM, disponibles para el uso de puntos flotantes. Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada. En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.

### <a name="register-volatility-and-preservation"></a>Volatilidad y conservación de los registros

En la siguiente tabla se explica el uso de cada registro en las llamadas de función:

||||
|-|-|-|
|Registro|Situación|Usar|
|RAX|Volátil|Registro de valor devuelto|
|RCX|Volátil|Primer argumento de entero|
|RDX|Volátil|Segundo argumento de entero|
|R8|Volátil|Tercer argumento de entero|
|R9|Volátil|Cuarto argumento de entero|
|R10:R11|Volátil|El llamador debe conservarlo según sea necesario; utilizado en instrucciones syscall/sysret|
|R12:R15|No volátil|El destinatario de la llamada debe conservarlo|
|RDI|No volátil|El destinatario de la llamada debe conservarlo|
|RSI|No volátil|El destinatario de la llamada debe conservarlo|
|RBX|No volátil|El destinatario de la llamada debe conservarlo|
|RBP|No volátil|Se puede usar como un puntero de marco; el destinatario de la llamada debe conservarlo según sea necesario|
|RSP|No volátil|Puntero de pila|
|XMM0, YMM0|Volátil|Primer argumento de FP; primer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM1, YMM1|Volátil|Segundo argumento de FP; segundo argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM2, YMM2|Volátil|Tercer argumento de FP; tercer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM3, YMM3|Volátil|Cuarto argumento de FP; cuarto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM4, YMM4|Volátil|El llamador debe conservarlo según sea necesario; quinto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM5, YMM5|Volátil|El llamador debe conservarlo según sea necesario; sexto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM6:XMM15, YMM6:YMM15|No volátil (XMM), volátil (mitad superior de YMM)|Lo debe conservar el destinatario. El llamador debe conservar los registros de YMM según sea necesario.|

En la salida y entrada de la función para las llamadas a la biblioteca en tiempo de ejecución de C y las llamadas del sistema de Windows, se espera que la marca de dirección del registro de marcas de CPU se borre.

## <a name="stack-usage"></a>Uso de la pila

Para obtener más información sobre la asignación de pila, la alineación, los tipos de función y los marcos de pila en x64, vea [Uso de la pila de x64](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prólogo y epílogo

Todas las funciones que asignan espacio de pila, llaman a otras funciones, guardan registros no volátiles o usan el control de excepciones deben tener un prólogo cuyos límites de dirección se describen en los datos de desenredado asociados a la entrada de la tabla de funciones correspondiente, así como epílogos en cada salida de una función. Para obtener más información sobre el código de prólogo y epílogo necesario en x64, vea [Prólogo y epílogo de x64](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>Control de excepciones x64

Para obtener información sobre las convenciones y estructuras de datos que se usan para implementar el control de excepciones estructurado y el comportamiento del control de excepciones de C++ en x64, vea [Control de excepciones en x64](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Elementos intrínsecos y ensamblado en línea

Una de las restricciones del compilador x64 es la falta de compatibilidad con el ensamblador en línea. Esto significa que las funciones que no se pueden escribir en C o C++ se tienen que crear como subrutinas o como funciones intrínsecas admitidas por el compilador. Algunas funciones son sensibles el rendimiento y otras no. Las funciones sensibles al rendimiento se deben implementar como funciones intrínsecas.

Los elementos intrínsecos que admite el compilador se describen en [Intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Formato de imagen

El formato de imagen ejecutable de x64 es PE32+. Las imágenes ejecutables (tanto DLL como EXE) están restringidas a un tamaño máximo de 2 gigabytes, por lo que se puede usar el direccionamiento relativo con un desplazamiento de 32 bits para tratar los datos de imagen estáticos. Estos datos incluyen la tabla de direcciones de importación, las constantes de cadena y los datos globales estáticos, entre otros.

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)
