---
title: . IF | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .IF
dev_langs:
- C++
helpviewer_keywords:
- .IF directive
ms.assetid: dccc7615-8fc7-4829-9f39-0ee405f6c1e3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7bd5ba5821b4dcfb2d088e31816f50540445018
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43691549"
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