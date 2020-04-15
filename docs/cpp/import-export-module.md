---
title: módulo, importar, exportar
ms.date: 12/12/2019
f1_keywords:
- module_cpp
- import_cpp
- export_cpp
helpviewer_keywords:
- modules [C++]
- modules [C++], import
- modules [C++], export
description: Utilice las declaraciones de importación y exportación para acceder y publicar tipos y funciones definidos en el módulo especificado.
ms.openlocfilehash: a765e9a406660d3c945ef3d70754178b0648458c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374111"
---
# <a name="module-import-export"></a>módulo, importar, exportar

Las declaraciones **module**, **import**y **export** están disponibles en C++20 y requieren el modificador del compilador [/experimental:module](../build/reference/experimental-module.md) junto con [/std:c++latest](../build/reference/std-specify-language-standard-version.md). Para obtener más información, consulte [Información general de los módulos en C++](modules-cpp.md).

## <a name="module"></a>module

Coloque una declaración de **módulo** al principio de un archivo de implementación de módulo para especificar que el contenido del archivo pertenece al módulo con nombre.

```cpp
module ModuleA;
```

## <a name="export"></a>exportar

Utilice una declaración de módulo de **exportación** para el archivo de interfaz principal del módulo, que debe tener la extensión **.ixx:**

```cpp
export module ModuleA;
```

En un archivo de interfaz, utilice el modificador **de exportación** en los nombres que están diseñados para formar parte de la interfaz pública:

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

int main() {
  Bar::f(); // OK
  Bar::d(); // OK
  Bar::internal_f(); // Ill-formed: error C2065: 'internal_f': undeclared identifier
}
```

Es posible que la palabra clave **export** no aparezca en un archivo de implementación de módulo. Cuando se aplica la **exportación** a un nombre de espacio de nombres, se exportan todos los nombres del espacio de nombres.

## <a name="import"></a>importación

Utilice una declaración de **importación** para hacer visibles los nombres de un módulo en el programa. La declaración de importación debe aparecer después de la declaración de módulo y después de cualquier directiva #include, pero antes de cualquier declaración en el archivo.

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

## <a name="remarks"></a>Observaciones

Tanto **la importación** como el **módulo** se tratan como palabras clave solo cuando aparecen al principio de una línea lógica:

```cpp

// OK:
module ;
module module-name
import :
import <
import "
import module-name
export module ;
export module module-name
export import :
export import <
export import "
export import module-name

// Error:
int i; module ;
```

**Microsoft Specific**

En Microsoft C++, la **importación** de tokens y el **módulo** siempre son identificadores y nunca palabras clave cuando se usan como argumentos para una macro.

### <a name="example"></a>Ejemplo

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Fin de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Información general de los módulos en C++](modules-cpp.md)
