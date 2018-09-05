---
title: XMMWORD. | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- XMMWORD
dev_langs:
- C++
helpviewer_keywords:
- XMMWORD directive
ms.assetid: 18026d32-5cab-403e-ad7e-382fb41aa9b8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7fbb578c5e168f53bc1b4e217713efa1ea329743
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689219"
---
# <a name="xmmword"></a>XMMWORD

Se usa para los operandos multimedios de 128 bits con las instrucciones MMX y SSE (XMM).

## <a name="syntax"></a>Sintaxis

> XMMWORD

## <a name="remarks"></a>Comentarios

`XMMWORD` está diseñado para representar el mismo tipo que [__m128](../../cpp/m128.md).

## <a name="example"></a>Ejemplo

```asm
    movdqa   xmm0, xmmword ptr [ebx]
```