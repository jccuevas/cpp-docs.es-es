---
title: Las herramientas del vinculador LNK4022 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4022
dev_langs:
- C++
helpviewer_keywords:
- LNK4022
ms.assetid: 890f487e-db98-45dd-a226-c7ccead82b1e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9e35974a72de349f94f2189f676b6dc955c48fab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4022"></a>Advertencia de las herramientas del vinculador LNK4022
no se puede encontrar a una coincidencia única para el símbolo 'símbolo'  
  
 LINK o LIB encontraron múltiples coincidencias para el símbolo no representativo dado y no se pudo resolver la ambigüedad. Se genera ningún archivo de salida (.exe, .dll, .exp o .lib). Esta advertencia va seguida de una advertencia [LNK4002](../../error-messages/tool-errors/linker-tools-warning-lnk4002.md) para cada Duplicar símbolo y por último, va seguido de un error irrecuperable [LNK1152](../../error-messages/tool-errors/linker-tools-error-lnk1152.md).  
  
 Para evitar esta advertencia, especifique el símbolo en su forma representativa. Ejecutar [DUMPBIN](../../build/reference/dumpbin-options.md) en el objeto para ver nombres representativos.