---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: de2aa99375f588d682b714632590ba8e0db8ddcb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50597228"
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