---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3bdb6af98aa71fef3d4af24091dc7463d917ce15
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915961"
---
# <a name="fpo"></a>.FPO

El. La Directiva FPO controla la emisión de registros de depuración en la sección o segmento. Debug $ F.

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
Indica el tipo de marco.  Vea [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-fpo_data) para obtener más información.

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
