---
title: atributo de importación embedded_idl
ms.date: 08/29/2019
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: 01948b171b20ad0a3bf3e7a41047f1fe3df185b0
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216327"
---
# <a name="embedded_idl-import-attribute"></a>atributo de importación embedded_idl

**C++Cuestión**

Especifica si la biblioteca de tipos se escribe en `.tlh` el archivo con el código generado por el atributo conservado.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **embedded_idl** [ **(** { **"emitidl"**  |  **"no_emitidl"** } **)** ]

### <a name="parameters"></a>Parámetros

**emitidl**\
La información de tipo importada de *Type-Library* está presente en el IDL generado para el proyecto con atributos. Este comportamiento es el predeterminado y está en vigor si no se especifica un parámetro en `embedded_idl`.

**"no_emitidl"** \
La información de tipo importada de la *biblioteca de tipos* no está presente en el IDL generado para el proyecto con atributos.

## <a name="example"></a>Ejemplo

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
