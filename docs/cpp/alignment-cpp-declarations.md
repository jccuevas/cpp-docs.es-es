---
title: Alineación (declaraciones de C++)
description: Cómo se especifica la alineación de datos en el modo modern C++.
ms.date: 05/30/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: b6e03ac2b89624a0eb6602183d4ff4bf8b518f8d
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450769"
---
# <a name="alignment-c-declarations"></a>Alineación (declaraciones de C++)

Una de las características de bajo nivel de C++ es la capacidad para especificar la alineación precisa de los objetos en la memoria para sacar el máximo partido de una arquitectura de hardware específica. De forma predeterminada, el compilador alinea los miembros de clase y estructura en su valor de tamaño: `bool` y `char` en los límites de 1 byte, `short` en límites de 2 bytes, `int`, `long`, y `float` en límites de 4 bytes y `long long`, `double`, y `long double` en límites de 8 bytes. En la mayoría de los escenarios, nunca tendrá que preocuparse por alineación porque la alineación predeterminada ya es óptima. En algunos casos, sin embargo, puede conseguir importantes mejoras de rendimiento o ahorros de memoria especificando una alineación personalizada para sus estructuras de datos. Antes de Visual Studio 2015 puede usar las palabras clave específicas de Microsoft `__alignof` y `declspec(alignas)` para especificar una alineación mayor que el valor predeterminado. A partir de Visual Studio 2015, debe utilizar el C ++ 11 palabras clave estándar [alignof y alignas](../cpp/alignof-and-alignas-cpp.md) para la portabilidad de código al máximo. Las nuevas palabras clave se comportan de la misma manera en segundo plano, como las extensiones específicas de Microsoft. La documentación de esas extensiones también se aplica a las nuevas palabras clave. Para obtener más información, consulte [operador __alignof](../cpp/alignof-operator.md) y [alinear](../cpp/align-cpp.md). El C++ estándar no especifica el comportamiento de empaquetado para la alineación en los límites de menores que el valor predeterminado del compilador para la plataforma de destino, por lo que deberá usar Microsoft #pragma [pack](../preprocessor/pack.md) en ese caso.

Use la [aligned_storage (clase)](../standard-library/aligned-storage-class.md) para la asignación de memoria de las estructuras de datos con alineaciones personalizadas. El [clase aligned_union](../standard-library/aligned-union-class.md) sirve para especificar la alineación de uniones con constructores no triviales o destructores.

## <a name="about-alignment"></a>Acerca de la alineación

La alineación es una propiedad de una dirección de memoria, expresada como el módulo de la dirección numérica a una potencia de 2. Por ejemplo, la dirección 0x0001103F módulo 4 es 3. Se dice que esa dirección alineada con 4n + 3, donde 4 indica la potencia de 2 elegida. La alineación de una dirección depende de la potencia de 2 elegida. El mismo módulo de dirección 8 es 7. Se dice que una dirección está alineada con X si su alineación es Xn+0.

Las CPU ejecutan instrucciones que operan en los datos almacenados en memoria. Los datos se identifican por sus direcciones de memoria. Un dato individual también tiene un tamaño. Llamamos a un dato *alineado naturalmente* si su dirección está alineada a su tamaño. Se llama *desalineados* en caso contrario. Por ejemplo, una referencia de punto flotante de 8 bytes se encuentra alineada naturalmente si la dirección que se utiliza para identificarlo tiene una alineación de 8 bytes.

## <a name="compiler-handling-of-data-alignment"></a>Control del compilador de alineación de datos

Los compiladores intentan realizar asignaciones de datos de forma que impide que un error de alineación de datos.

Para los tipos de datos simples, el compilador asigna direcciones que son múltiplos del tamaño en bytes del tipo de datos. Por ejemplo, el compilador asigna direcciones a variables de tipo `long` que sean múltiplos de 4, establecer la parte inferior de la dirección de 2 bits a cero.

El compilador también rellena estructuras de manera que alinea naturalmente cada elemento de la estructura. Considere la estructura `struct x_` en el ejemplo de código siguiente:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} MyStruct;
```

El compilador rellena esta estructura para aplicar la alineación de forma natural.

El ejemplo de código siguiente muestra cómo el compilador coloca la estructura rellenada en memoria:

```cpp
// Shows the actual memory layout
struct x_
{
   char a;            // 1 byte
   char _pad0[3];     // padding to put 'b' on 4-byte boundary
   int b;            // 4 bytes
   short c;          // 2 bytes
   char d;           // 1 byte
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4
}
```

1. Ambas declaraciones devuelven `sizeof(struct x_)` como 12 bytes.

1. La segunda declaración incluye dos elementos de relleno:

1. `char _pad0[3]` Para alinear el `int b` miembro en un límite de 4 bytes

1. `char _pad1[1]` Para alinear los elementos de la estructura de matriz `struct _x bar[3];`

1. El relleno alinea los elementos de `bar[3]` de forma que permita el acceso natural.

El siguiente ejemplo de código muestra la `bar[3]` diseño de matriz:

```Output
adr offset   element
------   -------
0x0000   char a;         // bar[0]
0x0001   char pad0[3];
0x0004   int b;
0x0008   short c;
0x000a   char d;
0x000b   char _pad1[1];

0x000c   char a;         // bar[1]
0x000d   char _pad0[3];
0x0010   int b;
0x0014   short c;
0x0016   char d;
0x0017   char _pad1[1];

0x0018   char a;         // bar[2]
0x0019   char _pad0[3];
0x001c   int b;
0x0020   short c;
0x0022   char d;
0x0023   char _pad1[1];
```

## <a name="see-also"></a>Vea también

[Alineación de estructuras de datos](https://en.wikipedia.org/wiki/Data_structure_alignment)
