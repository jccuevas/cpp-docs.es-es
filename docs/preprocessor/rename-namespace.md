---
title: rename_namespace | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_namespace attribute
ms.assetid: 45006d2b-36cd-4bec-98b9-3b8ec45299e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 966c6dda7e5e0bd28e78f37967397c3b64e4e55c
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808477"
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