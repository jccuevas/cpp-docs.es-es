---
title: Usar atexit | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1bb0c89c34b5107326a961e874289d20cbd2385c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="using-atexit"></a>Usar atexit
Con el [atexit](../c-runtime-library/reference/atexit.md) función, puede especificar una función de procesamiento de salida que se ejecuta antes de la finalización del programa. Los objetos estáticos no globales inicializados antes de la llamada a `atexit` se destruyen antes de la ejecución de la función de procesamiento de salida.  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)