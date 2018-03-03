---
title: Usar atexit | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7aec0e5aedb2d17e7d22b4f480eaef2be26413fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-atexit"></a>Usar atexit
Con el [atexit](../c-runtime-library/reference/atexit.md) función, puede especificar una función de procesamiento de salida que se ejecuta antes de la finalización del programa. Los objetos estáticos no globales inicializados antes de la llamada a `atexit` se destruyen antes de la ejecución de la función de procesamiento de salida.  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)