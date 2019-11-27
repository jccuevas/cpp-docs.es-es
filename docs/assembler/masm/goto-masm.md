---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397483"
---
# <a name="goto-masm"></a>GOTO (MASM)

Transfiere el ensamblado a la línea marcada **:** _macrolabel_.

## <a name="syntax"></a>Sintaxis

> **Goto** *macrolabel*

## <a name="remarks"></a>Comentarios

**Goto** solo se permite dentro de [macros](macro.md), [para](for-masm.md)los bloques, [FORC](forc.md), [REPEAT](repeat.md)y [While](while-masm.md) . El destino *macrolabel* debe ser la única directiva en la línea y debe ir precedido por un signo de dos puntos iniciales.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
