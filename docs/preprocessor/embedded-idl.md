---
title: embedded_idl | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- embedded_idl
dev_langs:
- C++
helpviewer_keywords:
- embedded_idl attribute
ms.assetid: f1c1c2e8-3872-4172-8795-8d1288a20452
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d7337595111b01ceeec53cc97f11ec2f35a081c5
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808347"
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

- **emitidl**: información de tipo importada de typelib estará presente en el archivo IDL generado para el proyecto con atributos.  Este es el valor predeterminado y estará en vigor si no se especifica un parámetro para `embedded_idl`.

- **no_emitidl**: información de tipo importada de typelib no estará presente en el archivo IDL generado para el proyecto con atributos.

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