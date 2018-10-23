---
title: rename_search_namespace | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- rename_search_namespace
dev_langs:
- C++
helpviewer_keywords:
- rename_search_namespace attribute
ms.assetid: 47c9d7fd-59dc-4c62-87a1-9011a0040167
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f0cc95851c4aa7127e690ec013b9d06d57f2730d
ms.sourcegitcommit: 0164af5615389ffb1452ccc432eb55f6dc931047
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49808893"
---
# <a name="renamesearchnamespace"></a>rename_search_namespace

**Específicos de C++**

Tiene la misma funcionalidad que el [rename_namespace](../preprocessor/rename-namespace.md) atributo pero se usa en las bibliotecas de tipos que usa el `#import` la directiva con la [auto_search](../preprocessor/auto-search.md) atributo.

## <a name="syntax"></a>Sintaxis

```
rename_search_namespace("NewName")
```

### <a name="parameters"></a>Parámetros

*NewName*<br/>
Nuevo nombre del espacio de nombres.

## <a name="remarks"></a>Comentarios

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)