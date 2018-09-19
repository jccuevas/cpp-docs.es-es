---
title: Error del compilador C3172 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3172
dev_langs:
- C++
helpviewer_keywords:
- C3172
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25c3b1fd9132c6b170fdf74b1619a35d83959f90
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46117645"
---
# <a name="compiler-error-c3172"></a>Error del compilador C3172

'nombre_de_módulo': no se puede especificar distintos atributos idl_module en un proyecto

[idl_module](../../windows/idl-module.md) atributos con el mismo nombre pero distintos `dllname` o `version` se encontraron parámetros en dos de los archivos en una compilación. Solo uno único `idl_module` atributo se puede especificar cada compilación.

Idéntico `idl_module` atributos se pueden especificar más de un archivo de código fuente.

Por ejemplo, si la siguiente `idl_module` se encontraron atributos:

```
// C3172.cpp
[module(name="MyMod")];
[ idl_module(name="x", dllname="file.dll", version="1.1") ];
int main() {}
```

Y luego,

```
// C3172b.cpp
// compile with: C3172.cpp
// C3172 expected
[ idl_module(name="x", dllname="file.dll", version="1.0") ];
```

el compilador generará el error C3172 (tenga en cuenta los valores de versión diferente).