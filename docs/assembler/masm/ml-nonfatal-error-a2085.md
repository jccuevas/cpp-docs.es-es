---
title: Error recuperable A2085 de ML | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2085
dev_langs:
- C++
helpviewer_keywords:
- A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 82f0a014810679f0b48f79198b1335240f5cd6a8
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/28/2018
---
# <a name="ml-nonfatal-error-a2085"></a>Error recuperable A2085 de ML
**instrucción o registrar que no se aceptan en el modo actual de CPU**  
  
 Se intentó utilizar una instrucción, el registro o la palabra clave que no era válido para el modo de procesador actual.  
  
 Por ejemplo, registros de 32 bits requieren [.386](../../assembler/masm/dot-386.md) o superior. Registros de control como CR0 requieren el modo privilegiado [386p](../../assembler/masm/dot-386p.md) o superior. Este error también se generarán para el **NEAR32**, **FAR32**, y **FLAT** keywords, que requieren. **386** o superior.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)