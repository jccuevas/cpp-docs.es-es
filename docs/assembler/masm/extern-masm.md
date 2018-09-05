---
title: EXTERN (MASM) | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- extern
dev_langs:
- C++
helpviewer_keywords:
- EXTERN directive
ms.assetid: 667d703d-3aaf-4139-a586-29bc5dab1aff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a9008e8c1153c0a9b06530b14e661436f7e62a9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693675"
---
# <a name="extern-masm"></a>EXTERN (MASM)

Define uno o más variables externas, etiquetas o símbolos que se denominan *nombre* cuyo tipo es *tipo*.

## <a name="syntax"></a>Sintaxis

> EXTERN [[*langtype*]] *nombre* [[(*altid*)]]: *tipo* [[, [[*langtype*]]  *nombre* [[(*altid*)]]: *tipo*]]...

## <a name="remarks"></a>Comentarios

El *tipo* puede ser [ABS](../../assembler/masm/operator-abs.md), que importa *nombre* como una constante. Igual que [EXTRN](../../assembler/masm/extrn.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>