---
title: .IF
ms.date: 08/30/2018
f1_keywords:
- .IF
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
ms.openlocfilehash: cf9c594d843c937dd2191bee2a7cebadbc615c82
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50483647"
---
# <a name="if"></a>.IF

Genera código que comprueba `condition1` (por ejemplo, AX > 7) y ejecuta el *instrucciones* si esa condición es true.

## <a name="syntax"></a>Sintaxis

> . IF condition1<br/>
> instrucciones<br/>
> [[. ELSEIF condition2<br/>
> instrucciones]]<br/>
> [[. ELSE<br/>
> instrucciones]]<br/>
> .ENDIF

## <a name="remarks"></a>Comentarios

Si un [. ELSE](../../assembler/masm/dot-else.md) sigue, sus instrucciones se ejecuta si la condición original era false. Tenga en cuenta que las condiciones se evalúan en tiempo de ejecución.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>