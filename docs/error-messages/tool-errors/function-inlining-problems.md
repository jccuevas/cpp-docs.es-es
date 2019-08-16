---
title: Problemas en la inclusión de funciones en línea
ms.date: 11/04/2016
helpviewer_keywords:
- /Ob1 C++ compiler option
- inline functions, problems
- -Ob1 C++ compiler option
- /Ob2 C++ compiler option
- -Ob2 C++ compiler option
- function inlining problems
ms.assetid: 65d59943-4b3c-4a43-aeb6-dccbf7686740
ms.openlocfilehash: f088b0f3ec94ad59c9c5576e6090a895bb88c3ad
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2019
ms.locfileid: "64856885"
---
# <a name="function-inlining-problems"></a>Problemas en la inclusión de funciones en línea

Si usas la inclusión de funciones, debe:

- Tiene las funciones en línea implementadas en el archivo de encabezado incluido.

- Tiene inserción activada (ON) en el archivo de encabezado.

```cpp
// LNK2019_function_inline.cpp
// compile with: /c
// post-build command: lib LNK2019_function_inline.obj
#include <stdio.h>
struct _load_config_used {
   void Test();
   void Test2() { printf("in Test2\n"); }
};

void _load_config_used::Test() { printf("in Test\n"); }
```

Y luego,

```cpp
// LNK2019_function_inline_2.cpp
// compile with: LNK2019_function_inline.lib
struct _load_config_used {
   void Test();
   void Test2();
};

int main() {
   _load_config_used x;
   x.Test();
   x.Test2();   // LNK2019
}
```

Si usas el `#pragma inline_depth` del compilador de la directiva, asegúrese de tener un valor de 2 o superior establecido. Un valor de cero, se desactivará inclusión entre líneas. Además, asegúrese de que usa el **/Ob1** o **/Ob2** opciones del compilador.

Mezcla de opciones de compilación en línea y no en línea en módulos diferentes, a veces puede causar problemas. Si se crea una biblioteca de C++ con la inclusión de funciones activado ([/Ob1](../../build/reference/ob-inline-function-expansion.md) o [/Ob2](../../build/reference/ob-inline-function-expansion.md)) pero el archivo de encabezado correspondiente que describe las funciones tiene desactivada (ninguna opción), obtendrá el error LNK2001. Las funciones no se insertan en el código del archivo de encabezado, pero puesto que no están en el archivo de biblioteca no hay ninguna dirección para resolver la referencia.

De forma similar, un proyecto que usa la inserción de funciones aún define las funciones en un archivo .cpp en lugar de en el encabezado de archivo también obtendrán LNK2019. El archivo de encabezado se incluye en todas partes lo considera apropiado, pero solo las funciones insertadas cuando el archivo .cpp pasa por el compilador; por lo tanto, el vinculador ve las funciones como externos sin resolver cuando se usa en otros módulos.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

Y entonces

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

Y entonces

```cpp
// LNK2019_FIP_2.cpp
// compile with: LNK2019_FIP.cpp
// LNK2019 expected
#include "LNK2019_FIP.h"
int main() {
   testclass testclsObject;

   // module cannot see the implementation of PublicStatMemFunc1
   testclsObject.PublicStatMemFunc1();
}
```

## <a name="see-also"></a>Vea también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)