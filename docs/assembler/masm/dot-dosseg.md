---
title: . DOSSEG | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693237"
---
# <a name="dosseg"></a>.DOSSEG

Ordena los segmentos de acuerdo con la convención de segmento de MS-DOS: código segmentos, a continuación, no en DGROUP en primer lugar y, a continuación, los segmentos en DGROUP.

## <a name="syntax"></a>Sintaxis

> .DOSSEG

## <a name="remarks"></a>Comentarios

Los segmentos DGROUP siguen este orden: segmentos que no BSS o pila, a continuación, segmentos BSS y, finalmente, segmentos de pila. Se utiliza principalmente para garantizar la compatibilidad de CodeView en programas independientes de MASM. Igual que [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>