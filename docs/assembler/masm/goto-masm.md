---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: a03cbda5a8ff64f6c167766f416e7744a5382ad5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62203091"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfiere el ensamblado a la línea marcada **:**_macrolabel_.

## <a name="syntax"></a>Sintaxis

> **GOTO** *macrolabel*

## <a name="remarks"></a>Comentarios

**GOTO** se permite únicamente dentro de [MACRO](macro.md), [para](for-masm.md), [FORZADA](forc.md), [repita](repeat.md), y [al](while-masm.md)bloques. El *macrolabel* debe ir precedido por un signo de dos puntos inicial y debe ser la única directiva en la línea de destino.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
