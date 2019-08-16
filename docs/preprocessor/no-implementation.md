---
title: no_implementation
ms.date: 11/04/2016
f1_keywords:
- no_implementation
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
ms.openlocfilehash: 26527ca69c66c73f5d41084dc42df5faa34481d3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409816"
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)