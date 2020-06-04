---
title: MMWORD
ms.date: 12/17/2019
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: fd3b9f40b7ff9fa4dae570e0ed906c13a9456424
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75311928"
---
# <a name="mmword"></a>MMWORD

Se utiliza para los operandos multimedia de 64 bits con instrucciones MMX y SSE (XMM).

## <a name="syntax"></a>Sintaxis

> **MMWORD**

## <a name="remarks"></a>Notas

**MMWORD** es un tipo.  Antes de que **MMWORD** se agregara a MASM, se podía conseguir una funcionalidad equivalente con:

```asm
    mov mm0, qword ptr [ebx]
```

Aunque ambas instrucciones funcionan en operandos de 64 bits, **QWord** es el tipo de los enteros sin signo de 64 bits y **MMWORD** es el tipo de un valor multimedia de 64 bits.

**MMWORD** está diseñado para representar el mismo tipo que [__m64](../../cpp/m64.md).

## <a name="example"></a>Ejemplo

```asm
    movq     mm0, mmword ptr [ebx]
```

## <a name="see-also"></a>Vea también

[Gramática BNF de MASM](masm-bnf-grammar.md)
