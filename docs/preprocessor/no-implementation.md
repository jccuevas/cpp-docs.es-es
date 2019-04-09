---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 26527ca69c66c73f5d41084dc42df5faa34481d3
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030546"
---
# <a name="noimplementation"></a>no_implementation
**Específicos de C++**

Suprime la generación del encabezado .tli, que contiene las implementaciones de las funciones miembro de contenedor.

## <a name="syntax"></a>Sintaxis

```
no_implementation
```

## <a name="remarks"></a>Comentarios

Si se especifica este atributo, el encabezado.tlh, con las declaraciones para exponer elementos de la biblioteca de tipos, se generará sin una instrucción `#include` para incluir el archivo de encabezado .tli.

Este atributo se utiliza junto con [implementation_only](../preprocessor/implementation-only.md).

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)