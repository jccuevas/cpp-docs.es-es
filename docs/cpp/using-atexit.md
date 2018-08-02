---
title: Usar atexit | Microsoft Docs
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
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467409"
---
# <a name="using-atexit"></a>Usar atexit
Con el [atexit](../c-runtime-library/reference/atexit.md) función, puede especificar una función de procesamiento de salida que se ejecuta antes de la finalización del programa. No hay objetos estáticos globales inicializados antes de la llamada a **atexit** se destruyen antes de la ejecución de la función de procesamiento de salida.  
  
## <a name="see-also"></a>Vea también  
 [Consideraciones de finalización adicionales](../cpp/additional-termination-considerations.md)