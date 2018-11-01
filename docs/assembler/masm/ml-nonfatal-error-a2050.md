---
title: Error recuperable A2050 de ML
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2050
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
ms.openlocfilehash: 59d08b9c2743a3b45633527bcc54b3e1c4d6a58c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50439720"
---
# <a name="ml-nonfatal-error-a2050"></a>Error recuperable A2050 de ML

**real o número de BCD no permitido**

Se usó no sea un número (real) de punto flotante o una constante decimal codificado en binario (BCD) como un inicializador de datos.

Se produjo alguna de las siguientes acciones:

- Se utilizó un número real o un BCD en una expresión.

- Un número real utilizado para inicializar una directiva distinta [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), o [TBYTE](../../assembler/masm/tbyte.md).

- Un BCD se usó para inicializar una directiva distinta `TBYTE`.

## <a name="see-also"></a>Vea también

[Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)<br/>