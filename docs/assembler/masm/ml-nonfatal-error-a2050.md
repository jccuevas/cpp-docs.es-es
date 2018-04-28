---
title: Error recuperable A2050 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2050
dev_langs:
- C++
helpviewer_keywords:
- A2050
ms.assetid: 16f3a58f-4bde-48f1-b0e3-2ed9612780a5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 159ed131c13166435114234b3b16a82cd4d41d1f
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
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