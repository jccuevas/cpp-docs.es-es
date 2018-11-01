---
title: EXTERN (MASM)
ms.date: 08/30/2018
f1_keywords:
- extern
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
ms.openlocfilehash: 30d1b3ae7c6676aeb97b91c7627da859525b9ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50497362"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Define uno o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es *tipo*.

## <a name="syntax"></a>Sintaxis

> EXTERN [[*langtype*]] *nombre* [[(*altid*)]]: *tipo* [[, [[*langtype*]]  *nombre* [[(*altid*)]]: *tipo*]]...

## <a name="remarks"></a>Comentarios

El *tipo* puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Igual que [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>