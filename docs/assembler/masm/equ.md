---
title: EQU | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 37509a39d2247649c2971932f402a18f3ac667d4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43681312"
---
# <a name="equ"></a>EQU

La primera directiva asigna un valor numérico de *expresión* a *nombre*.

## <a name="syntax"></a>Sintaxis

> *nombre* EQU *expresión*

> *nombre* EQU \< *texto*>

## <a name="remarks"></a>Comentarios

El *nombre* no se puede redefinir más adelante.

El segundo asigna la directiva especificado *texto* a *nombre*. El *nombre* se puede asignar otro *texto* más adelante. Consulte [TEXTEQU](../../assembler/masm/textequ.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>