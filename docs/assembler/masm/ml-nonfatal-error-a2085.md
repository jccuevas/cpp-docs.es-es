---
title: Error recuperable A2085 de ML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A2085
dev_langs: C++
helpviewer_keywords: A2085
ms.assetid: c2fef415-a32b-4249-896c-6d981fc6e327
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f987b775c13b0e477fd5c1d215d556069535a0fd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ml-nonfatal-error-a2085"></a>Error recuperable A2085 de ML
**instrucción o registrar que no se aceptan en el modo actual de CPU**  
  
 Se intentó utilizar una instrucción, el registro o la palabra clave que no era válido para el modo de procesador actual.  
  
 Por ejemplo, registros de 32 bits requieren [.386](../../assembler/masm/dot-386.md) o superior. Registros de control como CR0 requieren el modo privilegiado [386p](../../assembler/masm/dot-386p.md) o superior. Este error también se generarán para el **NEAR32**, **FAR32**, y **PLANO** keywords, que requieren. **386** o superior.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de error de ML](../../assembler/masm/ml-error-messages.md)