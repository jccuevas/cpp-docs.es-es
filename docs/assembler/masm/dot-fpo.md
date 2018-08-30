---
title: . FPO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 234ec5bd703a390d1e2ee60e48d99d346d4aad95
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203118"
---
# <a name="fpo"></a>.FPO
El archivo. Directiva de FPO controla la emisión de los registros de depuración a la sección o segmento de .debug$ F.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cdwLocals`  
 Número de variables locales, un valor de 32 bits sin signo.  
  
 `cdwParams`  
 Tamaño de los parámetros de DWORD, un valor de 16 bits sin signo.  
  
 *cbProlog*  
 Número de bytes en el código de prólogo de función, un valor de 8 bits sin signo.  
  
 `cbRegs`  
 Número de registros guardados.  
  
 `fUseBP`  
 Indica si se ha asignado el registro EBP. 0 o 1.  
  
 *cbFrame*  
 Indica el tipo de marco.  Consulte [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)