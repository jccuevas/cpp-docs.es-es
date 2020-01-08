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
description: Use declaraciones de importación y exportación para obtener acceso y publicar tipos y funciones definidos en el módulo especificado.
ms.openlocfilehash: ae28bce8e06840cafa5c92521f6e9a62aa5bfde6
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301462"
---
# <a name="module-import-export"></a>módulo, importar, exportar

Las declaraciones de **módulo**, **importación**y **exportación** están disponibles en c++ 20 y requieren el modificador de compilador [/experimental: module](../build/reference/experimental-module.md) junto con [/STD: C + + latest](../build/reference/std-specify-language-standard-version.md). Para obtener más información, vea [información general sobre C++los módulos de ](modules-cpp.md).

## <a name="module"></a>module

Coloque una declaración de **módulo** al principio de un archivo de implementación de módulo para especificar que el contenido del archivo pertenece al módulo con nombre.

```cpp
module ModuleA;
```

## <a name="export"></a>export

Use una declaración de **módulo de exportación** para el archivo de interfaz principal del módulo, que debe tener la extensión **. IXX**:

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

Es posible que la palabra clave **Export** no aparezca en un archivo de implementación de módulos. Cuando se aplica la **exportación** a un nombre de espacio de nombres, se exportan todos los nombres del espacio de nombres.

## <a name="import"></a>importación

Utilice una declaración de **importación** para que los nombres de un módulo estén visibles en el programa. La declaración de importación debe aparecer después de la declaración de módulo y después de cualquier directiva de #include, pero antes de cualquier declaración en el archivo.

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

## <a name="remarks"></a>Notas

Tanto la **importación** como el **módulo** se tratan como palabras clave solo cuando aparecen al principio de una línea lógica:

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

**Específicos de Microsoft**

En Microsoft C++, los módulos **Import** y **Module** son siempre identificadores y nunca palabras clave cuando se usan como argumentos para una macro.

### <a name="example"></a>Ejemplo

```cpp
#define foo(…) __VA_ARGS__
foo(
import // Always an identifier, never a keyword
)
```

**Fin de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Información general sobre los módulos deC++](modules-cpp.md)
