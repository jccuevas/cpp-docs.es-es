---
title: GOTO (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- goto
dev_langs:
- C++
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0be678e2d39389cbc551c386c1890f799124b5b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43694021"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfiere el ensamblado a la línea marcada **:**_macrolabel_.

## <a name="syntax"></a>Sintaxis

> **GOTO** *macrolabel*

## <a name="remarks"></a>Comentarios

**GOTO** se permite únicamente dentro de [MACRO](macro.md), [para](for-masm.md), [FORZADA](forc.md), [repita](repeat.md), y [al](while-masm.md)bloques. El *macrolabel* debe ir precedido por un signo de dos puntos inicial y debe ser la única directiva en la línea de destino.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
