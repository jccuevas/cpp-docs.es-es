---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 5f0c23ad8b8d81f888616042ee5d6ba5bc63bd44
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412879"
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
