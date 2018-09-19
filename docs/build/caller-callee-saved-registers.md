---
title: Registros guardados del llamador y destinatario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e8e877387dbb5b0be865e11017a3ac71a0c38faa
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45707660"
---
# <a name="callercallee-saved-registers"></a>Registros guardados del llamador y del destinatario

Destruyen los registros RAX, RCX, RDX, R8, R9, R10, R11 se consideran volátiles y se deben considerar en las llamadas de función (a menos que en caso contrario, seguridad-opuestas por análisis como la optimización de todo el programa).

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14 y R15 se consideran no volátiles y deben guardarse y restaurarse con una función que los usa.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)