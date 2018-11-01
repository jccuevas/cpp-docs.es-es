---
title: .DOSSEG
ms.date: 08/30/2018
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 28b3e351030ee83693c0fec5568aacf9b4b77c27
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639444"
---
# <a name="dosseg"></a>.DOSSEG

Ordena los segmentos de acuerdo con la convención de segmento de MS-DOS: código segmentos, a continuación, no en DGROUP en primer lugar y, a continuación, los segmentos en DGROUP.

## <a name="syntax"></a>Sintaxis

> .DOSSEG

## <a name="remarks"></a>Comentarios

Los segmentos DGROUP siguen este orden: segmentos que no BSS o pila, a continuación, segmentos BSS y, finalmente, segmentos de pila. Se utiliza principalmente para garantizar la compatibilidad de CodeView en programas independientes de MASM. Igual que [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>