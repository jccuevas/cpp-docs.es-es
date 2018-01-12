---
title: . FPO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: .FPO
dev_langs: C++
helpviewer_keywords: .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 61d9209b5cf817d89e9e017626222a9cc73e209e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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