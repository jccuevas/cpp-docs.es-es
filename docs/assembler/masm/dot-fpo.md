---
title: . FPO | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be5e20716ff414eea3eddc8490e2a3f82adeb777
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687750"
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