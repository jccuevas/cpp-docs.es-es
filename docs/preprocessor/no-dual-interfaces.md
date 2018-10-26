---
title: no_dual_interfaces | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_dual_interfaces
dev_langs:
- C++
helpviewer_keywords:
- no_dual_interfaces attribute
ms.assetid: 9acd5d9d-4a49-4cdc-9470-73a2c23cf512
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6dcf63933a54983fcf98e35acce533670dc74ed4
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070964"
---
# <a name="nodualinterfaces"></a>no_dual_interfaces
**Específicos de C++**

Cambia la manera en que el compilador genera las funciones de contenedor para los métodos de interfaz dual.

## <a name="syntax"></a>Sintaxis

```
no_dual_interfaces
```

## <a name="remarks"></a>Comentarios

Normalmente, el contenedor llamará al método a través de la tabla de funciones virtuales para la interfaz. Con **no_dual_interfaces**, el contenedor en su lugar llama `IDispatch::Invoke` para invocar el método.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)