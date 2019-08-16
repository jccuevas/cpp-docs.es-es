---
title: rename_namespace
ms.date: 10/18/2018
f1_keywords:
- rename_namespace
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
ms.openlocfilehash: 7b3917a7114ca44d092f10a7831bb35bc64e9387
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62179768"
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)