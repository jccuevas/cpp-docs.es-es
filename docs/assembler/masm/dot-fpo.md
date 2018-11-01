---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570517"
---
# <a name="fpo"></a>.FPO

El archivo. Directiva de FPO controla la emisión de los registros de depuración a la sección o segmento de .debug$ F.

## <a name="syntax"></a>Sintaxis

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*,  *cbFrame*)

### <a name="parameters"></a>Parámetros

*cdwLocals*<br/>
Número de variables locales, un valor de 32 bits sin signo.

*cdwParams*<br/>
Tamaño de los parámetros de DWORD, un valor de 16 bits sin signo.

*cbProlog*<br/>
Número de bytes en el código de prólogo de función, un valor de 8 bits sin signo.

*cbRegs*<br/>
Número de registros guardados.

*fUseBP*<br/>
Indica si se ha asignado el registro EBP. 0 o 1.

*cbFrame*<br/>
Indica el tipo de marco.  Consulte [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) para obtener más información.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>