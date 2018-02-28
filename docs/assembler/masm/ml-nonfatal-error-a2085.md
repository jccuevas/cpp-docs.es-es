---
title: Error recuperable A2085 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 29d0d58e5cd65c16c848b3cc05e10b9f57488639
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="ml-nonfatal-error-a2085"></a>Error recuperable A2085 de ML
**instrucción o registrar que no se aceptan en el modo actual de CPU**  
  
 Se intentó utilizar una instrucción, el registro o la palabra clave que no era válido para el modo de procesador actual.  
  
 Por ejemplo, registros de 32 bits requieren [.386](../../assembler/masm/dot-386.md) o superior. Registros de control como CR0 requieren el modo privilegiado [386p](../../assembler/masm/dot-386p.md) o superior. Este error también se generarán para el **NEAR32**, **FAR32**, y **FLAT** keywords, que requieren. **386** o superior.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)