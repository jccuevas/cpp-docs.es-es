---
title: módulo, importar, exportar
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
ms.openlocfilehash: ee1d50a76a3304359c0771aa0174968439f5faa4
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273626"
---
# <a name="module-import-export"></a>módulo, importar, exportar

Las palabras clave **Module**, **Import**y **Export** están disponibles en c++ 20 y requieren el modificador de compilador [/experimental: module](../build/reference/experimental-module.md) junto con [/STD: C + + latest](../build/reference/std-specify-language-standard-version.md). Para obtener más información, vea [información general sobre C++los módulos de ](modules-cpp.md).

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
