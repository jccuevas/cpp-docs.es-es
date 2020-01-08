---
title: XMMWORD
ms.date: 12/17/2019
f1_keywords:
- XMMWORD
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
ms.openlocfilehash: 1116729883bf9b1b9342b30332bab5de6ba59015
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75319117"
---
# <a name="xmmword"></a>XMMWORD

Se utiliza para los operandos multimedia de 128 bits con instrucciones MMX y SSE (XMM).

## <a name="syntax"></a>Sintaxis

> **XMMWORD**

## <a name="remarks"></a>Notas

**XMMWORD** está diseñado para representar el mismo tipo que [__m128](../../cpp/m128.md).

## <a name="example"></a>Ejemplo

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```

## <a name="see-also"></a>Vea también

[Gramática BNF de MASM](masm-bnf-grammar.md)
