---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 650c69be17c9271c343360edbb90f093841a1047
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398256"
---
# <a name="fpo-32-bit-masm"></a>. FPO (MASM de 32 bits)

El **.** La Directiva FPO controla la emisión de registros de depuración en la sección o segmento. Debug $ F. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **. FPO** (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parámetros

\ *cdwLocals*
Número de variables locales, un valor de bit 32 sin signo.

\ *cdwParams*
Tamaño de los parámetros en DWORDs, un valor de 16 bits sin signo.

\ *cbProlog*
Número de bytes en el código de prólogo de la función, un valor de 8 bits sin signo.

\ *cbRegs*
Número de registros guardados.

\ *fUseBP*
Indica si se ha asignado el registro EBP. 0 o 1.

\ *cbFrame*
Indica el tipo de marco.  Consulte [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) para obtener más información.

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
