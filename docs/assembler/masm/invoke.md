---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 853bc9cd22d866357a4cd2d695beccc3efc20acf
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703960"
---
# <a name="invoke-32-bit-masm"></a>INVOKE (MASM de 32 bits)

Llama al procedimiento en la dirección proporcionada por la *expresión*, pasando los argumentos en la pila o en registros según las convenciones de llamada estándar del tipo de lenguaje. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> INVOCAr *expresión* [[, *argumentos*]]

## <a name="remarks"></a>Comentarios

Cada argumento que se pasa al procedimiento puede ser una expresión, un par de registros o una expresión de dirección (una expresión precedida por `ADDR`).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>