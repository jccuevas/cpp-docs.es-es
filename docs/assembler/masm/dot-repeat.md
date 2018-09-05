---
title: . REPITA | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8856ed0e1d86277a413baac2c56e5c5ca2ea9ff0
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687957"
---
# <a name="repeat"></a>.REPEAT

Genera código que se repite la ejecución del bloque de *instrucciones* hasta `condition` pasa a ser true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), que se convierte en true cuando CX es cero, se puede sustituir por [. Hasta que](../../assembler/masm/dot-until.md). El `condition` es opcional con **. UNTILCXZ**.

## <a name="syntax"></a>Sintaxis

> .REPEAT<br/>
> instrucciones<br/>
> . Hasta que la condición

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>