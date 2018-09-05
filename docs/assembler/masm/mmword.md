---
title: MMWORD. | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- MMWORD
dev_langs:
- C++
helpviewer_keywords:
- MMWORD directive
ms.assetid: b4c5a104-9078-4fb4-afc3-d1e63abe562a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7314c6d0861195e312c7f72481d2e195e041965d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679239"
---
# <a name="mmword"></a>MMWORD

Se usa para los operandos multimedios de 64 bits con las instrucciones MMX y SSE (XMM).

## <a name="syntax"></a>Sintaxis

> MMWORD

## <a name="remarks"></a>Comentarios

`MMWORD` es un tipo.  Antes de MMWORD se agrega a MASM, una funcionalidad equivalente se podría haber conseguido con:

```asm
    mov mm0, qword ptr [ebx]
```

Aunque ambas instrucciones funcionan en los operandos de 64 bits, `QWORD` es el tipo de enteros sin signo de 64 bits y `MMWORD` es el tipo para un valor multimedia de 64 bits.

`MMWORD` está diseñado para representar el mismo tipo que [__m64](../../cpp/m64.md).

## <a name="example"></a>Ejemplo

```asm
    movq     mm0, mmword ptr [ebx]
```