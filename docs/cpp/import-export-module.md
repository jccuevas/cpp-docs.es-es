---
title: módulo, importación y exportación
ms.date: 07/15/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Use la instrucción Import para tener acceso a los tipos y funciones definidos en el módulo especificado.
ms.openlocfilehash: fbb9c45ec816c859edb4df38ad67dc7778247e87
ms.sourcegitcommit: 7b039b5f32f6c59be6c6bb1cffafd69c3bfadd35
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2019
ms.locfileid: "68537791"
---
# <a name="module-import-export"></a>módulo, importación y exportación

Las palabras clave **Module**, **Import**y **Export** están disponibles en c++ 20 y requieren el `/experimental:modules` modificador del compilador junto con `/std:c++latest`. Para obtener más información, vea [información general sobre C++los módulos de ](modules-cpp.md).

## <a name="module"></a>module

Use la instrucción **Module** al principio de un archivo de implementación de módulo para especificar que el contenido del archivo pertenece al módulo con nombre. 

```cpp
module ModuleA;
```

## <a name="export"></a>exportar

Use la instrucción **Export Module** para el archivo de interfaz principal del módulo, que debe tener la extensión **. IXX**:

```cpp
export module ModuleA;
```

En un archivo de interfaz, use el modificador de **exportación** en los nombres diseñados para formar parte de la interfaz pública:

```cpp
// ModuleA.ixx

export module ModuleA;

namespace Bar
{
   export int f();
   export double d();
   double internal_f(); // not exported
}
```

Los nombres no exportados no son visibles para el código que importa el módulo:

```cpp
//MyProgram.cpp

import module ModuleA;

void main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Es posible que la palabra clave **Export** no aparezca en un archivo de implementación de módulos. Cuando se aplica el modificador de **exportación** a un nombre de espacio de nombres, se exportan todos los nombres del espacio de nombres.

## <a name="import"></a>importación

Use la instrucción **Import** para que los nombres de un módulo estén visibles en el programa. La instrucción Import debe aparecer después de la instrucción Module y después de cualquier directiva de #include, pero antes de cualquier declaración en el archivo.

```cpp
module ModuleA;

#include "custom-lib.h"
import std.core;
import std.regex;
import ModuleB;

// begin declarations here:
template <class T>
class Baz
{...};
```

## <a name="see-also"></a>Vea también
[Información general sobre los módulos deC++](modules-cpp.md)
