---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039883"
---
# <a name="renamenamespace"></a>rename_namespace

**Específicos de C++**

Cambia el espacio de nombres que incluye el contenido de la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```
rename_namespace("NewName")
```

### <a name="parameters"></a>Parámetros

*NewName*<br/>
Nuevo nombre del espacio de nombres.

## <a name="remarks"></a>Comentarios

Toma un único argumento, *NewName*, que especifica el nuevo nombre para el espacio de nombres.

Para quitar el espacio de nombres, use el [no_namespace](../preprocessor/no-namespace.md) atributo en su lugar.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)