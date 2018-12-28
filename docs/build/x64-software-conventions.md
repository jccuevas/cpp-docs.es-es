---
title: x64 convenciones de software
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: eea2059a8c06a8ba4d032b87fb41d7d51bc8eac2
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627311"
---
# <a name="x64-software-conventions"></a>x64 convenciones de software

Esta sección describe la metodología de convención de llamada para x64, la extensión de 64 bits para el x86 C++ arquitectura.

## <a name="overview-of-x64-calling-conventions"></a>Información general sobre las convenciones de llamada de x64

Dos diferencias importantes entre x86 y x64 son la capacidad de direccionamiento de 64 bits y un conjunto simple de 64 bits de 16 registros de uso general. Dado el conjunto de registros expandida, x64 usa el [__fastcall](../cpp/fastcall.md) convención de llamada y un modelo de control de excepciones basado en RISC. El `__fastcall` convención usa registros para los cuatro primeros argumentos y el marco de pila para pasar argumentos adicionales. Para obtener más información sobre la x64 convención de llamada, incluido el uso del registro, los parámetros de pila, devolver valores y desenredo de pila, vea [x64 convención de llamada](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Habilitar la optimización de x64

La opción del compilador siguiente le ayuda a optimizar su aplicación para x64:

- [/favor (Optimizar para valores específicos de la arquitectura)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Tipos y almacenamiento

Esta sección describe la enumeración y el almacenamiento de tipos de datos para el x64 arquitectura.

### <a name="scalar-types"></a>tipos escalares

Aunque es posible tener acceso a datos con ninguna alineación, se recomienda para alinear los datos en su límite natural o un múltiplo, para evitar la pérdida de rendimiento. Las enumeraciones son enteros constantes y se tratan como enteros de 32 bits. La tabla siguiente describe la definición de tipo y el almacenamiento recomendado para los datos, ya que pertenece a la alineación con los siguientes valores de alineación:

- Byte - 8 bits

- Palabra: 16 bits

- Palabra doble - 32 bits

- Quadword - 64 bits

- Octaword - 128 bits

|||||
|-|-|-|-|
|Tipo escalar|Tipo de datos C|Tamaño de almacenamiento (en bytes)|Alineación recomendada|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Palabra|
|**UINT16**|**unsigned short**|2|Palabra|
|**INT32**|**int**, **largo**|4|Palabra doble|
|**UINT32**|**int sin signo, unsigned long**|4|Palabra doble|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**unsigned __int64**|8|Quadword|
|**FP32 (precisión simple)**|**float**|4|Palabra doble|
|**FP64 (precisión doble)**|**double**|8|Quadword|
|**PUNTERO**|__\*__|8|Quadword|
|**__m64**|**__m64 (struct)**|8|Quadword|
|**__m128**|**__m128 struct**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregados y uniones

Otros tipos, como matrices, estructuras y uniones, tienen requisitos de alineación más estrictos que garantizan la coherencia agregada y union almacenamiento y recuperación de datos. Estas son las definiciones de matriz, estructura y unión:

- Matriz

   Contiene un grupo ordenado de objetos de datos adyacentes. Cada objeto se denomina un *elemento*. Todos los elementos dentro de una matriz tienen el mismo tamaño y tipo de datos.

- Estructura

   Contiene un grupo ordenado de objetos de datos. A diferencia de los elementos de una matriz, los objetos de datos dentro de una estructura pueden tener diferentes tipos de datos y tamaños. Cada objeto de datos en una estructura se denomina un *miembro*.

- Unión

   Objeto que contiene cualquier miembro de un conjunto de miembros con nombre. Los miembros del conjunto con nombre pueden ser de cualquier tipo. El almacenamiento asignado para una unión es igual que el almacenamiento necesario para el miembro de unión, más cualquier relleno necesario para la alineación mayor.

En la tabla siguiente se muestra la alineación sugerida encarecidamente para los miembros de estructuras y uniones escalares.

||||
|-|-|-|
|Tipo escalar|Tipo de datos C|Alineación requerida|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Palabra|
|**UINT16**|**unsigned short**|Palabra|
|**INT32**|**int**, **largo**|Palabra doble|
|**UINT32**|**int sin signo, unsigned long**|Palabra doble|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (precisión simple)**|**float**|Palabra doble|
|**FP64 (precisión doble)**|**double**|Quadword|
|**PUNTERO**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 (struct)**|Quadword|
|**__m128**|**__m128 struct**|Octaword|

Se aplican las siguientes reglas de alineación de agregados:

- La alineación de una matriz es igual que la alineación de uno de los elementos de la matriz.

- La alineación del principio de una estructura o unión es la alineación máxima de cualquier miembro individual. Cada miembro dentro de la estructura o unión debe colocarse en su alineación apropiada, tal como se define en la tabla anterior, lo que puede requerir relleno interno implícito, dependiendo del miembro anterior.

- Tamaño de la estructura debe ser un múltiplo integral de su alineación, que puede requerir relleno después del último miembro. Dado que las estructuras y uniones se pueden agrupar en matrices, cada elemento de matriz de una estructura o unión debe empiezan y terminan en la correcta alineación determinada previamente.

- Es posible alinear los datos de tal forma que sean mayores que los requisitos de alineación, siempre se mantienen las reglas anteriores.

- Un compilador individual puede ajustar el empaquetado de una estructura por motivos de tamaño. Por ejemplo [/Zp (alineación de miembros de Struct)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.

### <a name="examples-of-structure-alignment"></a>Ejemplos de alineación de estructuras

Los siguientes cuatro ejemplos de declaran que una estructura alineada o unión y las cifras correspondientes muestran el diseño de esa estructura o unión en la memoria. Cada columna de una figura representa un byte de memoria y el número de la columna indica el desplazamiento de ese byte. El nombre de la segunda fila de cada figura corresponde al nombre de una variable en la declaración. Las columnas sombreadas indican el relleno que se requiere para lograr la alineación especificada.

#### <a name="example-1"></a>Ejemplo 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Diseño de estructura de ejemplo 1 de conversión de AMD](../build/media/vcamd_conv_ex_1_block.png "diseño de estructura de ejemplo 1 de conversión de AMD")

#### <a name="example-2"></a>Ejemplo 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Diseño de estructura de ejemplo 2 de conversión de AMD](../build/media/vcamd_conv_ex_2_block.png "diseño de estructura de ejemplo 2 de conversión de AMD")

#### <a name="example-3"></a>Ejemplo 3

```C
// Total size = 22 bytes, alignment = 4 bytes (doubleword).

_declspec(align(4)) struct {
    char a;       // +0; size = 1 byte
    short b;      // +2; size = 2 bytes
    char c;       // +4; size = 1 byte
    int d;        // +8; size = 4 bytes
}
```

![Diseño de estructura de ejemplo 2 de conversión de AMD](../build/media/vcamd_conv_ex_3_block.png "diseño de estructura de ejemplo 2 de conversión de AMD")

#### <a name="example-4"></a>Ejemplo 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Ejemplo 4 de conversión AMD layouit unión](../build/media/vcamd_conv_ex_4_block.png "layouit union de ejemplo 4 de conversión de AMD")

### <a name="bitfields"></a>Campos de bits

Campos de bits de estructura se limitan a 64 bits y puede ser de tipo con signo int, int sin signo, int64 o int64 sin signo. Campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo de bits para la alineación del tipo siguiente. Por ejemplo, los campos de bits de enteros no pueden cruzar un límite de 32 bits.

### <a name="conflicts-with-the-x86-compiler"></a>Entra en conflicto con el x86 compilador

Tipos de datos que sean mayores que 4 bytes no se alinean automáticamente en la pila cuando se usa el x86 compilador para compilar una aplicación. Dado que la arquitectura para la x86 compilador es una pila alineada de 4 bytes, nada más de 4 bytes, por ejemplo, un entero de 64 bits, no se alinean automáticamente en una dirección de 8 bytes.

Trabajar con datos no alineados tiene dos consecuencias.

- Puede tardar más tiempo en obtener acceso a ubicaciones sin alineación que se tarda en obtener acceso a ubicaciones alineadas.

- Las ubicaciones sin alinear no se puede usar en las operaciones de interbloqueos.

Si necesita una alineación más estricta, use `__declspec(align(N))` en las declaraciones de variable. Esto hace que el compilador alinear dinámicamente la pila para cumplir sus especificaciones. Sin embargo, ajustar la pila dinámicamente en tiempo de ejecución puede provocar una ejecución más lenta de la aplicación.

## <a name="register-usage"></a>Uso de registros

La arquitectura proporciona para 16 registros de uso general (en adelante como registros de enteros), así como 16 registros de XMM/YMM de x64 registra disponibles para su uso de punto flotante. Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada. En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.

### <a name="register-volatility-and-preservation"></a>Registrar la volatilidad y conservación

En la siguiente tabla se explica el uso de cada registro en las llamadas de función:

||||
|-|-|-|
|Registro|Estado|Uso|
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
|XMM6:XMM15, YMM6:YMM15|No volátil (XMM), volátil (mitad superior de YMM)|Deben conservarse por el destinatario. El llamador debe conservar los registros de YMM según sea necesario.|

En la salida de la función y en la entrada de la función a las llamadas de biblioteca en tiempo de ejecución de C y las llamadas del sistema de Windows, la marca de dirección en la CPU register marcas se espera que se puede borrar.

## <a name="stack-usage"></a>Uso de la pila

Para obtener más información sobre la asignación de la pila, alineación, tipos de función y marcos de pila en x64, consulte [x64 de uso de la pila](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prólogo y epílogo

Cada función que asigna espacio de pila, llama a otras funciones, guarda los registros no volátiles o usa el control de excepciones debe tener un prólogo cuyos límites de direcciones se describen en los datos de desenredo asociados con la entrada de la tabla de función correspondiente y epílogos en cada salida a una función. Para obtener más información sobre el prólogo necesario y el código de epílogo en x64, consulte [x64 prólogo y epílogo](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>x64 control de excepciones

Para obtener información sobre las convenciones y las estructuras de datos que se usan para implementar el control de excepciones estructurado y el comportamiento en el x64 del control de excepciones de C++, vea [x64 control de excepciones](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Ensamblado intrínseco y en línea

Una de las restricciones para el x64 compilador es no compatibles con el ensamblador alineado. Esto significa que las funciones que no se puede escribir en C o C++ tendrán que escribirse como subrutinas o funciones intrínsecas compatibles con el compilador. Algunas funciones son sensibles al rendimiento, mientras que otros no. Las funciones de sensibles al rendimiento deben implementarse como funciones intrínsecas.

En el que se describen las funciones intrínsecas compatibles con el compilador [intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Formato de imagen

El x64 es el formato de imagen ejecutable PE32 +. Imágenes ejecutables (archivos DLL y exe) están restringidas a un tamaño máximo de 2 gigabytes, por lo que las direcciones relativas con un desplazamiento de 32 bits pueden usarse para datos de imagen estática de direcciones. Estos datos incluyen la tabla de importar direcciones, las constantes de cadena, datos globales estáticos y así sucesivamente.

## <a name="see-also"></a>Vea también

[Convenciones de llamada](../cpp/calling-conventions.md)