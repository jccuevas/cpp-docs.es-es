---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814324"
---
# <a name="stacksize"></a>STACKSIZE

Establece el tamaño de la pila en bytes.

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Comentarios

Una manera equivalente a establecer la pila es con la [asignaciones de la pila](stack-stack-allocations.md) (/stack) opción. Consulte la documentación de esa opción para obtener más información sobre la *reservar* y `commit` argumentos.

Esta opción no tiene ningún efecto en los archivos DLL.

## <a name="see-also"></a>Vea también

[Reglas para instrucciones de definición de módulos](rules-for-module-definition-statements.md)
