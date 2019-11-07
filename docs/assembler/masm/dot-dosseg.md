---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: 8f0388c3df9804c0cdb105162a962a44fe207345
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703311"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG ((MASM de 32 bits)

Ordena los segmentos según la Convención de segmentos de MS-DOS: CODE First y, a continuación, segmentos que no están en DGROUP y, a continuación, Segments en DGROUP. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> .DOSSEG

## <a name="remarks"></a>Comentarios

Los segmentos de DGROUP siguen este orden: los segmentos no están en el BSS o la pila, los segmentos de BSS y, por último, los segmentos de pila. Se utiliza principalmente para garantizar la compatibilidad con CodeView en programas independientes de MASM. Igual que [dosseg (](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>