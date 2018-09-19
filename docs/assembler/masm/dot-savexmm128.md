---
title: . SAVEXMM128 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .SAVEXMM128
dev_langs:
- C++
helpviewer_keywords:
- .SAVEXMM128 directive
ms.assetid: 551eb472-b8d0-47b1-8d82-995d1f485723
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0d44855d3449000c588f7e840753bd734af4b1af
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43689912"
---
# <a name="savexmm128"></a>.SAVEXMM128

Cualquiera genera un `UWOP_SAVE_XMM128` o un `UWOP_SAVE_XMM128_FAR` desenredar la entrada de código para el registro XMM especificado y el desplazamiento actual del prólogo de desplazamiento. MASM elegirá la codificación más eficaz.

## <a name="syntax"></a>Sintaxis

> . savexmm128 xmmreg, desplazamiento

## <a name="remarks"></a>Comentarios

. Savexmm128 permite a los usuarios de ml64.exe especificar cómo se desenreda una función de marco y solo se permite en el prólogo, que se extiende desde el [PROC](../../assembler/masm/proc.md) declaración de marco para el [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) directiva. Estas directivas no generan código; solo generan `.xdata` y `.pdata`. . Savexmm128 debe ir precedido de instrucciones que implementan las acciones que no resulte dañada. Es una buena práctica para ajustar las directivas de desenredado y el código que están diseñadas para desenredo en una macro para asegurarse de acuerdo.

*desplazamiento* debe ser un múltiplo de 16.

Para obtener más información, consulte [MASM para x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>