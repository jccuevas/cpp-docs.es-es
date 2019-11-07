---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703795"
---
# <a name="fpo-32-bit-masm"></a>. FPO (MASM de 32 bits)

El. La Directiva FPO controla la emisión de registros de depuración en la sección o segmento. Debug $ F. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parámetros

*cdwLocals*<br/>
Número de variables locales, un valor de bit 32 sin signo.

*cdwParams*<br/>
Tamaño de los parámetros en DWORDs, un valor de 16 bits sin signo.

*cbProlog*<br/>
Número de bytes en el código de prólogo de la función, un valor de 8 bits sin signo.

*cbRegs*<br/>
Número de registros guardados.

*fUseBP*<br/>
Indica si se ha asignado el registro EBP. 0 o 1.

*cbFrame*<br/>
Indica el tipo de marco.  Vea [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) para obtener más información.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
