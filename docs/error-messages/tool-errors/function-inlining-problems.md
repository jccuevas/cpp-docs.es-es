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
ms.openlocfilehash: cb4653bd2f03683b9abad1eea0e9ffa88222090e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184247"
---
# <a name="function-inlining-problems"></a>Problemas en la inclusión de funciones en línea

Si usa la inclusión de funciones, debe:

- Tenga las funciones insertadas implementadas en el archivo de encabezado que incluya.

- Tenga activada la inserción en el archivo de encabezado.

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

Si usa la Directiva de compilador de `#pragma inline_depth`, asegúrese de que tiene un valor de 2 o superior establecido. Si el valor es cero, se desactivará la inserción. Asegúrese también de que está usando las opciones del compilador **/ob1** o **/OB2** .

En ocasiones, la combinación de opciones de compilación inline y no alineadas en módulos diferentes puede causar problemas. Si una C++ biblioteca se crea con la inserción de funciones activada ([/ob1](../../build/reference/ob-inline-function-expansion.md) o [/OB2](../../build/reference/ob-inline-function-expansion.md)), pero el archivo de encabezado correspondiente que describe las funciones tiene la inserción desactivada (ninguna opción), obtendrá el error LNK2001. Las funciones no se insertan en el código del archivo de encabezado, pero como no están en el archivo de biblioteca, no hay ninguna dirección para resolver la referencia.

Del mismo modo, un proyecto que usa la inclusión de funciones que define las funciones en un archivo. cpp, en lugar de en el archivo de encabezado, también obtendrá LNK2019. El archivo de encabezado se incluye en cualquier lugar que se considere adecuado, pero las funciones solo se insertan cuando el archivo. cpp pasa a través del compilador; por lo tanto, el vinculador ve las funciones como externas sin resolver cuando se usa en otros módulos.

```cpp
// LNK2019_FIP.h
struct testclass {
   void PublicStatMemFunc1(void);
};
```

y, a continuación,

```cpp
// LNK2019_FIP.cpp
// compile with: /c
#include "LNK2019_FIP.h"
inline void testclass::PublicStatMemFunc1(void) {}
```

y, a continuación,

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

## <a name="see-also"></a>Consulte también

[Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)
