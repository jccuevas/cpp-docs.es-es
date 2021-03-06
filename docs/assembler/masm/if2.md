---
title: IF1 y IF2
ms.date: 11/21/2019
f1_keywords:
- IF2
- IF1
helpviewer_keywords:
- IF2 directive
- IF2 directive
ms.assetid: a0f75564-b51b-4e39-ad3b-f7421e7ecad6
ms.openlocfilehash: 60f8b0dcedb61ac06de929aff300845e342d7cfc
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317323"
---
# <a name="if1-and-if2"></a>IF1 y IF2

El bloque **If1** se evalúa en el primer paso del ensamblado.

El bloque **IF2** se evalúa en cada paso del ensamblado si la **opción: SETIF2** es **true**.

## <a name="syntax"></a>Sintaxis

> **IF1;;**

> **IF2;;**

## <a name="remarks"></a>Notas

Vea [si](if-masm.md) para obtener la sintaxis completa.

A diferencia de la versión 5,1, MASM 6,1 y versiones posteriores realizan la mayor parte de su trabajo en su primer paso, realiza tantos pasos posteriores como sea necesario. En cambio, MASM 5,1 siempre ensambla en dos fases de origen. Como resultado, puede que tenga que revisar o eliminar algunas construcciones dependientes del paso en MASM 6,1 y versiones posteriores.

### <a name="two-pass-directives"></a>Directivas de dos pasos

Para garantizar la compatibilidad, MASM 6,1 y versiones posteriores admiten directivas 5,1 que hacen referencia a dos fases. Estos incluyen **. ERR1**, **. ERR2**, **If1**, **IF2**, **ELSEIF1**y **ELSEIF2**. En el caso de las construcciones de segundo paso, debe especificar la [opción SETIF2](option-masm.md). Sin la **opción SETIF2**, **IF2** y **.** Las directivas de Err2 causan un error:

```output
.ERR2 not allowed : single-pass assembler
```

MASM 6,1 y versiones posteriores administran de forma diferente las construcciones de primera paso. Trata el **. Directiva ERR1** como **. ERR**y la directiva **If1** como **si**.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
