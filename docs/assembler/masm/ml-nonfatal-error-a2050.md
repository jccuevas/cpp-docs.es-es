---
title: Error recuperable A2050 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 887a18ee274b3e09624a07e214f235333e2a9665
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2050"></a>Error recuperable A2050 de ML
**real o no se permite un número de BCD**  
  
 Un número (real) de punto flotante o una constante decimal codificado en binario (BCD) usó distinto de como un inicializador de datos.  
  
 Se produjo uno de los siguientes:  
  
-   Un número real o un BCD se usó en una expresión.  
  
-   Un número real utilizado para inicializar una directiva distinta de [DWORD](../../assembler/masm/dword.md), [QWORD](../../assembler/masm/qword.md), o [TBYTE](../../assembler/masm/tbyte.md).  
  
-   Se usó un BCD para inicializar una directiva distinta de `TBYTE`.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)