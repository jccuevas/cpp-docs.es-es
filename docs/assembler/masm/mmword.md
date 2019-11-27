---
title: MMWORD
ms.date: 08/30/2018
f1_keywords:
- MMWORD
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
ms.openlocfilehash: d4378c1435df09f249fe7f55dabd4bd0f43f6100
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397173"
---
# <a name="mmword"></a>MMWORD

Se utiliza para los operandos multimedia de 64 bits con instrucciones MMX y SSE (XMM).

## <a name="syntax"></a>Sintaxis

> **MMWORD**

## <a name="remarks"></a>Comentarios

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
