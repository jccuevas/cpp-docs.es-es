---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: e8213052dce8d84d62f90d4bc2653435c2b31434
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398223"
---
# <a name="if-32-bit-masm"></a>. IF (MASM de 32 bits)

Genera código que prueba *condition1* (por ejemplo, AX > 7) y ejecuta las *instrucciones* si esa condición es true. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **. Si** *condition1*\
> *instrucciones*\
> ⟦ **.\ ELSEIF** *condition2*
> *instrucciones*⟧ \
> ⟦ **. ELSE**\
> *instrucciones*⟧ \
> **.ENDIF**

## <a name="remarks"></a>Comentarios

Si es [. Más adelante,](../../assembler/masm/dot-else.md) sus instrucciones se ejecutan si la condición original fuera falsa. Tenga en cuenta que las condiciones se evalúan en tiempo de ejecución.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
