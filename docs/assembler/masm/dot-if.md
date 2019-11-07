---
title: .IF
ms.date: 11/05/2019
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: 83c9ff588e2fe273e24e1d0b1c16517c5eee3365
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703775"
---
# <a name="if-32-bit-masm"></a>. IF (MASM de 32 bits)

Genera código que prueba `condition1` (por ejemplo, AX > 7) y ejecuta las *instrucciones* si esa condición es true. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> . Si condition1<br/>
> instrucciones<br/>
> [[. ELSEIF condition2<br/>
> instrucciones]]<br/>
> [[. DEMÁS<br/>
> instrucciones]]<br/>
> .ENDIF

## <a name="remarks"></a>Comentarios

Si es [. Más adelante,](../../assembler/masm/dot-else.md) sus instrucciones se ejecutan si la condición original fuera falsa. Tenga en cuenta que las condiciones se evalúan en tiempo de ejecución.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>