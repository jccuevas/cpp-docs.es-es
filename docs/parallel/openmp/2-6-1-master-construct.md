---
title: 2.6.1 master construcción | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c092064b-ea57-4d4e-9c99-a004d65656fe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a60a8df380fdcc0052d8fe2d070c8d926bcb28f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689561"
---
# <a name="261-master-construct"></a>2.6.1 master (Construcción)
El **maestro** directiva identifica una construcción que especifica un bloque estructurado que se ejecuta en el subproceso principal del equipo. La sintaxis de la **maestro** directiva es como sigue:  
  
```  
#pragma omp master new-linestructured-block  
```  
  
 Otros subprocesos en el equipo no ejecuten el bloque estructurado asociado. No hay ninguna barrera implícita, ya sea en la entrada o salida de la master (construcción).