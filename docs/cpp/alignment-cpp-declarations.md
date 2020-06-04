---
title: Alignment
description: Cómo se especifica la alineación de datos C++en moderno.
ms.date: 12/11/2019
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
ms.openlocfilehash: 45b22742394a0b1c159e8b8102a26802a2441929
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076111"
---
# <a name="alignment"></a>Alignment

Una de las características de bajo nivel de C++ es la capacidad para especificar la alineación precisa de los objetos en la memoria para sacar el máximo partido de una arquitectura de hardware específica. De forma predeterminada, el compilador alinea los miembros de clase y struct en su valor de tamaño: `bool` y `char` en límites de 1 byte, `short` en límites de 2 bytes, `int`, `long`y `float` en límites de 4 bytes, y `long long`, `double`y `long double` en límites de 8 bytes.

En la mayoría de los escenarios, nunca tendrá que preocuparse de la alineación, ya que la alineación predeterminada ya es óptima. En algunos casos, sin embargo, puede lograr mejoras significativas en el rendimiento o ahorrar memoria si especifica una alineación personalizada para las estructuras de datos. Antes de Visual Studio 2015 podría usar las palabras clave específicas de Microsoft `__alignof` y `declspec(alignas)` para especificar una alineación mayor que la predeterminada. A partir de Visual Studio 2015, debe usar las palabras clave de C++ 11 estándar **aligna** y **alignas** para obtener la máxima portabilidad del código. Las nuevas palabras clave se comportan de la misma manera bajo el capó que las extensiones específicas de Microsoft. La documentación de esas extensiones también se aplica a las nuevas palabras clave. Para obtener más información, vea [__Alignof operador](../cpp/alignof-operator.md) y [align](../cpp/align-cpp.md). El C++ estándar no especifica el comportamiento de empaquetado para la alineación en los límites menores que el valor predeterminado del compilador para la plataforma de destino, por lo que todavía necesitará usar Microsoft #pragma [Pack](../preprocessor/pack.md) en ese caso.

Utilice la [clase aligned_storage](../standard-library/aligned-storage-class.md) para la asignación de memoria de estructuras de datos con alineaciones personalizadas. La [clase aligned_union](../standard-library/aligned-union-class.md) es para especificar la alineación de las uniones con constructores o destructores no triviales.

## <a name="alignment-and-memory-addresses"></a>Alineación y direcciones de memoria

La alineación es una propiedad de una dirección de memoria, expresada como el módulo de la dirección numérica a una potencia de 2. Por ejemplo, la dirección 0x0001103F módulo 4 es 3. Se dice que esa dirección está alineada con 4N + 3, donde 4 indica la potencia elegida de 2. La alineación de una dirección depende de la potencia elegida de 2. El mismo módulo de dirección 8 es 7. Se dice que una dirección está alineada con X si su alineación es Xn+0.

Las CPU ejecutan instrucciones que operan en los datos almacenados en memoria. Los datos se identifican por sus direcciones en la memoria. Un único dato también tiene un tamaño. Se llama a un dato de referencia *Naturally aligned* si su dirección está alineada con su tamaño. En caso contrario, se llama *desalineado* . Por ejemplo, una referencia de punto flotante de 8 bytes se alinea de forma natural si la dirección usada para identificarla tiene una alineación de 8 bytes.

## <a name="compiler-handling-of-data-alignment"></a>Control del compilador de la alineación de datos

Los compiladores intentan realizar asignaciones de datos de forma que se evite la alineación incorrecta de los datos.

Para los tipos de datos simples, el compilador asigna direcciones que son múltiplos del tamaño en bytes del tipo de datos. Por ejemplo, el compilador asigna direcciones a variables de tipo `long` que son múltiplos de 4, estableciendo los 2 bits inferiores de la dirección en cero.

El compilador también rellena las estructuras de una manera que alinea naturalmente cada elemento de la estructura. Tenga en cuenta la estructura `struct x_` en el ejemplo de código siguiente:

```cpp
struct x_
{
   char a;     // 1 byte
   int b;      // 4 bytes
   short c;    // 2 bytes
   char d;     // 1 byte
} bar[3];
```

El compilador rellena esta estructura para aplicar la alineación de forma natural.

En el ejemplo de código siguiente se muestra cómo el compilador coloca la estructura acolchada en la memoria:

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
} bar[3];
```

Ambas declaraciones devuelven `sizeof(struct x_)` como 12 bytes.

La segunda declaración incluye dos elementos de relleno:

1. `char _pad0[3]` para alinear el miembro de `int b` en un límite de 4 bytes.

1. `char _pad1[1]` para alinear los elementos de matriz de la estructura `struct _x bar[3];` en un límite de cuatro bytes.

El relleno alinea los elementos de `bar[3]` de forma que permitan el acceso natural.

En el ejemplo de código siguiente se muestra el diseño de la matriz `bar[3]`:

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

## <a name="alignof-and-alignas"></a>alignof y alignas

El especificador de tipo **alignas** es una manera C++ portátil y estándar de especificar la alineación personalizada de variables y tipos definidos por el usuario. El operador **align** es igualmente una forma estándar y portátil de obtener la alineación de un tipo o variable especificado.

## <a name="example"></a>Ejemplo

Puede usar **alignas** en una clase, un struct o una Unión, o en miembros individuales. Cuando se encuentran varios especificadores **alignas** , el compilador elegirá el más estricto (el que tiene el valor más grande).

```cpp
// alignas_alignof.cpp
// compile with: cl /EHsc alignas_alignof.cpp
#include <iostream>

struct alignas(16) Bar
{
    int i;       // 4 bytes
    int n;      // 4 bytes
    alignas(4) char arr[3];
    short s;          // 2 bytes
};

int main()
{
    std::cout << alignof(Bar) << std::endl; // output: 16
}
```

## <a name="see-also"></a>Consulte también

[Alineación de la estructura de datos](https://en.wikipedia.org/wiki/Data_structure_alignment)
