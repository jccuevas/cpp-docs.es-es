---
title: Convenciones de software x64
ms.date: 12/17/2018
helpviewer_keywords:
- x64 coding conventions
- Visual C++, x64 calling conventions
ms.assetid: 750f3d97-1706-4840-b2fc-41a007329a08
ms.openlocfilehash: 11d29b6c31ccecfe5b9c51c2f9311213bd4a6732
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865605"
---
# <a name="x64-software-conventions"></a>Convenciones de software x64

En esta sección se C++ describe la metodología de Convención de llamada para x64, la extensión de 64 bits a la arquitectura x86.

## <a name="overview-of-x64-calling-conventions"></a>Información general sobre las convenciones de llamada x64

Dos diferencias importantes entre x86 y x64 son la capacidad de direccionamiento de 64 bits y un conjunto plano de registros de 16 64 bits para uso general. Dado el conjunto de registros expandido, x64 usa la Convención de llamada de [__fastcall](../cpp/fastcall.md) y un modelo de control de excepciones basado en RISC. La Convención de `__fastcall` usa registros para los primeros cuatro argumentos y el marco de pila para pasar argumentos adicionales. Para obtener información detallada sobre la Convención de llamada x64, incluido el uso de registros, los parámetros de la pila, los valores devueltos y el desenredado de la pila, vea [Convención de llamada x64](x64-calling-convention.md).

## <a name="enable-optimization-for-x64"></a>Habilitar optimización para x64

La siguiente opción del compilador le ayuda a optimizar la aplicación para x64:

- [/favor (Optimizar para valores específicos de la arquitectura)](../build/reference/favor-optimize-for-architecture-specifics.md)

## <a name="types-and-storage"></a>Tipos y almacenamiento

En esta sección se describe la enumeración y el almacenamiento de tipos de datos para la arquitectura x64.

### <a name="scalar-types"></a>Tipos escalares

Aunque es posible tener acceso a los datos con cualquier alineación, se recomienda alinear los datos en su límite natural, o en algunos varios, para evitar la pérdida de rendimiento. Las enumeraciones son enteros constantes y se tratan como enteros de 32 bits. En la tabla siguiente se describe la definición de tipo y el almacenamiento recomendado para los datos, ya que pertenecen a la alineación usando los siguientes valores de alineación:

- Bytes de 8 bits

- De texto de 16 bits

- Palabra-32 bits

- Quadword-64 bits

- Octaword-128 bits

|||||
|-|-|-|-|
|Tipo escalar|C, tipo de datos|Tamaño de almacenamiento (en bytes)|Alineación recomendada|
|**INT8**|**char**|1|Byte|
|**UINT8**|**unsigned char**|1|Byte|
|**INT16**|**short**|2|Word|
|**UINT16**|**unsigned short**|2|Word|
|**INT32**|**int**, **Long**|4|Palabra|
|**UINT32**|**unsigned int, unsigned Long**|4|Palabra|
|**INT64**|**__int64**|8|Quadword|
|**UINT64**|**unsigned __int64**|8|Quadword|
|**FP32 (precisión sencilla)**|**float**|4|Palabra|
|**FP64 (precisión doble)**|**double**|8|Quadword|
|**PUNTERO**|__\*__|8|Quadword|
|**__m64**|**__m64 struct**|8|Quadword|
|**__m128**|**__m128 struct**|16|Octaword|

### <a name="aggregates-and-unions"></a>Agregados y uniones

Otros tipos, como matrices, estructuras y uniones, tienen requisitos de alineación más estrictos que garantizan un almacenamiento de conjunto y una Unión coherentes y la recuperación de datos. Estas son las definiciones de matriz, estructura y Unión:

- Array

   Contiene un grupo ordenado de objetos de datos adyacentes. Cada objeto se denomina *elemento*. Todos los elementos de una matriz tienen el mismo tamaño y tipo de datos.

- Estructura

   Contiene un grupo ordenado de objetos de datos. A diferencia de los elementos de una matriz, los objetos de datos de una estructura pueden tener distintos tamaños y tipos de datos. Cada objeto de datos de una estructura se denomina *miembro*.

- Union

   Objeto que contiene cualquiera de un conjunto de miembros con nombre. Los miembros del conjunto con nombre pueden ser de cualquier tipo. El almacenamiento asignado para una Unión es igual al almacenamiento necesario para el miembro más grande de esa Unión, además de cualquier relleno necesario para la alineación.

En la tabla siguiente se muestra la alineación muy sugerida para los miembros escalares de uniones y estructuras.

||||
|-|-|-|
|Tipo escalar|C, tipo de datos|Alineación necesaria|
|**INT8**|**char**|Byte|
|**UINT8**|**unsigned char**|Byte|
|**INT16**|**short**|Word|
|**UINT16**|**unsigned short**|Word|
|**INT32**|**int**, **Long**|Palabra|
|**UINT32**|**unsigned int, unsigned Long**|Palabra|
|**INT64**|**__int64**|Quadword|
|**UINT64**|**unsigned __int64**|Quadword|
|**FP32 (precisión sencilla)**|**float**|Palabra|
|**FP64 (precisión doble)**|**double**|Quadword|
|**PUNTERO**|<strong>\*</strong>|Quadword|
|**__m64**|**__m64 struct**|Quadword|
|**__m128**|**__m128 struct**|Octaword|

Se aplican las siguientes reglas de alineación agregada:

- La alineación de una matriz es la misma que la alineación de uno de los elementos de la matriz.

- La alineación del principio de una estructura o una Unión es la alineación máxima de cualquier miembro individual. Cada miembro de la estructura o Unión debe colocarse en su alineación adecuada, tal y como se define en la tabla anterior, lo que puede requerir un relleno interno implícito, dependiendo del miembro anterior.

- El tamaño de la estructura debe ser un múltiplo entero de su alineación, lo que puede requerir el relleno después del último miembro. Puesto que las estructuras y las uniones se pueden agrupar en matrices, cada elemento de matriz de una estructura o Unión debe comenzar y finalizar en la alineación adecuada previamente determinada.

- Es posible alinear los datos de tal forma que sean mayores que los requisitos de alineación, siempre y cuando se mantengan las reglas anteriores.

- Un compilador individual puede ajustar el empaquetado de una estructura por motivos de tamaño. Por ejemplo [,/ZP (alineación de miembros de estructura)](../build/reference/zp-struct-member-alignment.md) permite ajustar el empaquetado de estructuras.

### <a name="examples-of-structure-alignment"></a>Ejemplos de alineación de estructuras

Los cuatro ejemplos siguientes declaran una estructura alineada o una Unión, y las figuras correspondientes muestran el diseño de esa estructura o unión en la memoria. Cada columna de una ilustración representa un byte de memoria y el número de la columna indica el desplazamiento de ese byte. El nombre de la segunda fila de cada ilustración se corresponde con el nombre de una variable en la declaración. Las columnas sombreadas indican el relleno necesario para lograr la alineación especificada.

#### <a name="example-1"></a>Ejemplo 1

```C
// Total size = 2 bytes, alignment = 2 bytes (word).

_declspec(align(2)) struct {
    short a;      // +0; size = 2 bytes
}
```

![Ejemplo 1 de la conversión de AMD diseño de estructura](../build/media/vcamd_conv_ex_1_block.png "Ejemplo 1 de la conversión de AMD diseño de estructura")

#### <a name="example-2"></a>Ejemplo 2

```C
// Total size = 24 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) struct {
    int a;       // +0; size = 4 bytes
    double b;    // +8; size = 8 bytes
    short c;     // +16; size = 2 bytes
}
```

![Ejemplo de conversión de AMD 2 diseño de estructura](../build/media/vcamd_conv_ex_2_block.png "Ejemplo de conversión de AMD 2 diseño de estructura")

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

![Ejemplo de conversión de AMD 2 diseño de estructura](../build/media/vcamd_conv_ex_3_block.png "Ejemplo de conversión de AMD 2 diseño de estructura")

#### <a name="example-4"></a>Ejemplo 4

```C
// Total size = 8 bytes, alignment = 8 bytes (quadword).

_declspec(align(8)) union {
    char *p;      // +0; size = 8 bytes
    short s;      // +0; size = 2 bytes
    long l;       // +0; size = 4 bytes
}
```

![Ejemplo de conversión AMD 4 Union layouit](../build/media/vcamd_conv_ex_4_block.png "Ejemplo de conversión AMD 4 Union layouit")

### <a name="bitfields"></a>Campos de bits

Los campos de bits de estructura se limitan a 64 bits y pueden ser de tipo signed int, unsigned int, Int64 o unsigned Int64. Los campos de bits que cruzan el límite de tipos omitirán bits para alinear el campo de bits con la alineación de tipo siguiente. Por ejemplo, los campos de bits enteros no pueden cruzar un límite de 32 bits.

### <a name="conflicts-with-the-x86-compiler"></a>Conflictos con el compilador de x86

Los tipos de datos de más de 4 bytes no se alinean automáticamente en la pila cuando se usa el compilador de x86 para compilar una aplicación. Dado que la arquitectura del compilador de x86 es una pila alineada de 4 bytes, algo mayor de 4 bytes, por ejemplo, un entero de 64 bits, no se puede alinear automáticamente a una dirección de 8 bytes.

Trabajar con datos sin alinear tiene dos implicaciones.

- Puede tardar más tiempo en obtener acceso a ubicaciones no alineadas de las que se tarda en acceder a ubicaciones alineadas.

- Las ubicaciones no alineadas no se pueden usar en operaciones de interbloqueo.

Si necesita una alineación más estricta, use `__declspec(align(N))` en las declaraciones de variables. Esto hace que el compilador Alinee dinámicamente la pila para cumplir sus especificaciones. Sin embargo, el ajuste dinámico de la pila en tiempo de ejecución puede ralentizar la ejecución de la aplicación.

## <a name="register-usage"></a>Registro de uso

La arquitectura x64 proporciona 16 registros de uso general (en adelante denominados registros de entero), así como 16 registros de XMM/YMM disponibles para el uso de punto flotante. Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada. En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.

### <a name="register-volatility-and-preservation"></a>Registro de volatilidad y preservación

En la siguiente tabla se explica el uso de cada registro en las llamadas de función:

||||
|-|-|-|
|Register|Status|Uso|
|RAX|Volatile|Registro de valor devuelto|
|RCX|Volatile|Primer argumento de entero|
|RDX|Volatile|Segundo argumento de entero|
|R8|Volatile|Tercer argumento de entero|
|R9|Volatile|Cuarto argumento de entero|
|R10:R11|Volatile|El llamador debe conservarlo según sea necesario; utilizado en instrucciones syscall/sysret|
|R12:R15|No volátil|El destinatario de la llamada debe conservarlo|
|RDI|No volátil|El destinatario de la llamada debe conservarlo|
|RSI|No volátil|El destinatario de la llamada debe conservarlo|
|RBX|No volátil|El destinatario de la llamada debe conservarlo|
|RBP|No volátil|Se puede usar como un puntero de marco; el destinatario de la llamada debe conservarlo según sea necesario|
|RSP|No volátil|Puntero de pila|
|XMM0, YMM0|Volatile|Primer argumento de FP; primer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM1, YMM1|Volatile|Segundo argumento de FP; segundo argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM2, YMM2|Volatile|Tercer argumento de FP; tercer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM3, YMM3|Volatile|Cuarto argumento de FP; cuarto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM4, YMM4|Volatile|El llamador debe conservarlo según sea necesario; quinto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM5, YMM5|Volatile|El llamador debe conservarlo según sea necesario; sexto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM6:XMM15, YMM6:YMM15|No volátil (XMM), volátil (mitad superior de YMM)|El destinatario de la llamada debe conservarlo. El llamador debe conservar los registros de YMM según sea necesario.|

En las llamadas a la biblioteca en tiempo de ejecución de C y a las llamadas del sistema de Windows, se espera que la marca de dirección del registro de marcas de CPU se borre.

## <a name="stack-usage"></a>Uso de la pila

Para más información sobre la asignación de pila, la alineación, los tipos de función y los marcos de pila en x64, consulte uso de la [pila de x64](stack-usage.md).

## <a name="prolog-and-epilog"></a>Prólogo y epílogo

Cada función que asigna espacio de pila, llama a otras funciones, guarda registros no volátiles o usa el control de excepciones debe tener un prólogo cuyos límites de dirección se describen en los datos de desenredado asociados a la entrada de la tabla de funciones respectiva y los errores en los registros cada salida a una función. Para obtener más información sobre el prólogo y el código de epílogo necesarios en x64, vea el [prólogo y el epílogo x64](prolog-and-epilog.md).

## <a name="x64-exception-handling"></a>Control de excepciones x64

Para obtener información sobre las convenciones y estructuras de datos que se usan para implementar C++ el control estructurado de excepciones y el comportamiento del control de excepciones en x64, vea control de excepciones [x64](exception-handling-x64.md).

## <a name="intrinsics-and-inline-assembly"></a>Ensamblados intrínsecos y en línea

Una de las restricciones del compilador x64 es no tener compatibilidad con el ensamblador en línea. Esto significa que las funciones que no se pueden escribir en C++ C o que se deben escribir como subrutinas o como funciones intrínsecas admitidas por el compilador. Algunas funciones distinguen el rendimiento y otras no. Las funciones que afectan al rendimiento deben implementarse como funciones intrínsecas.

Los intrínsecos admitidos por el compilador se describen en [intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="image-format"></a>Formato de imagen

El formato de imagen ejecutable x64 es PE32 +. Las imágenes ejecutables (tanto las dll como los archivos. exe) están restringidas a un tamaño máximo de 2 gigabytes, por lo que el direccionamiento relativo con un desplazamiento de 32 bits se puede usar para tratar los datos de imagen estáticos. Estos datos incluyen la tabla de direcciones de importación, las constantes de cadena, los datos globales estáticos, etc.

## <a name="see-also"></a>Consulte también

[Convenciones de llamada](../cpp/calling-conventions.md)
