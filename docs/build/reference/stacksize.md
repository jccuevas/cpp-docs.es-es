---
title: STACKSIZE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- STACKSIZE
dev_langs:
- C++
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7d9b61febedde1a2647df6312a8588b08c6bdad7
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705567"
---
# <a name="stacksize"></a>STACKSIZE

Establece el tamaño de la pila en bytes.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Comentarios

Una manera equivalente a establecer la pila es con la [asignaciones de la pila](../../build/reference/stack-stack-allocations.md) (/stack) opción. Consulte la documentación de esa opción para obtener más información sobre la *reservar* y `commit` argumentos.

Esta opción no tiene ningún efecto en los archivos DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)