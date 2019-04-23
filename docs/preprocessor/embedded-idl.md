---
title: embedded_idl
ms.date: 10/18/2018
f1_keywords:
- embedded_idl
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
ms.openlocfilehash: c46924d2757d01a934c21a70f23e6556f6a10fd3
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034094"
---
# <a name="embeddedidl"></a>embedded_idl

**Específicos de C++**

Especifica que la biblioteca de tipos se escriba en el archivo .tlh, conservando el código generado por el atributo.

## <a name="syntax"></a>Sintaxis

```
embedded_idl[("param")]
```

### <a name="parameters"></a>Parámetros

*param*<br/>
Puede ser uno de dos valores:

- **emitidl**: Información de tipo importada de typelib estará presente en el archivo IDL generado para el proyecto con atributos.  Este es el valor predeterminado y estará en vigor si no se especifica un parámetro para `embedded_idl`.

- **no_emitidl**: Información de tipo importada de typelib no estará presente en el archivo IDL generado para el proyecto con atributos.

## <a name="example"></a>Ejemplo

```cpp
// import_embedded_idl.cpp
// compile with: /LD
#include <windows.h>
[module(name="MyLib2")];
#import "\school\bin\importlib.tlb" embedded_idl("no_emitidl")
```

## <a name="remarks"></a>Comentarios

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)