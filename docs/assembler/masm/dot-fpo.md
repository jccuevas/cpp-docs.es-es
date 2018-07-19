---
title: . FPO | Documentos de Microsoft
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
ms.openlocfilehash: df5185c0dc699764427989b2f46345d90ded1729
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055943"
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
 Tamaño de los parámetros de valores DWORD, un valor de 16 bits sin signo.  
  
 *cbProlog*  
 Número de bytes en el código de prólogo de función, un valor de 8 bits sin signo.  
  
 `cbRegs`  
 Número de registros guardados.  
  
 `fUseBP`  
 Indica si se ha asignado el registro EBP. 0 ó 1.  
  
 *cbFrame*  
 Indica el tipo de marco.  Vea [FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352) para obtener más información.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de directivas](../../assembler/masm/directives-reference.md)