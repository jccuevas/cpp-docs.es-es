---
title: Registros guardados del llamador y destinatario
ms.date: 11/04/2016
ms.assetid: 0533bd4b-d6bb-4ce1-8201-495e16870cbb
ms.openlocfilehash: f34fbfff8e6c61b5d568c073f6b7da2a12e34535
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50654706"
---
# <a name="callercallee-saved-registers"></a>Registros guardados del llamador y del destinatario

Destruyen los registros RAX, RCX, RDX, R8, R9, R10, R11 se consideran volátiles y se deben considerar en las llamadas de función (a menos que en caso contrario, seguridad-opuestas por análisis como la optimización de todo el programa).

Los registros RBX, RBP, RDI, RSI, RSP, R12, R13, R14 y R15 se consideran no volátiles y deben guardarse y restaurarse con una función que los usa.

## <a name="see-also"></a>Vea también

[Convención de llamada](../build/calling-convention.md)