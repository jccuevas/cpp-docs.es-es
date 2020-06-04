---
title: Error del compilador C3172
ms.date: 11/04/2016
f1_keywords:
- C3172
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
ms.openlocfilehash: 1da2676d660d23e3fb71b56263779b1f1edacbf9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761743"
---
# <a name="compiler-error-c3172"></a>Error del compilador C3172

' module_name ': no se pueden especificar distintos atributos de idl_module en un proyecto

se encontraron [idl_module](../../windows/idl-module.md) atributos con el mismo nombre pero con distintos parámetros de `dllname` o `version` en dos de los archivos de una compilación. Solo se puede especificar un atributo de `idl_module` único por compilación.

Se pueden especificar atributos idénticos `idl_module` en más de un archivo de código fuente.

Por ejemplo, si se encuentran los siguientes atributos de `idl_module`:

```cpp
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

Y luego,

```cpp
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

el compilador generaría C3172 (tenga en cuenta los diferentes valores de versión).
