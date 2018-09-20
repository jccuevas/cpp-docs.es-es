---
title: 2.6.2 critical (construcción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: c46ecd00-b4a2-4a5e-ba92-288c329e773a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e51bd425999081c7a06a7d5692dbea16c887fa0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46417857"
---
# <a name="262-critical-construct"></a>2.6.2 critical (Construcción)

El **críticos** directiva identifica una construcción que limita la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la **críticos** directiva es como sigue:

```
#pragma omp critical [(name)]  new-linestructured-block
```

Opcional *nombre* puede utilizarse para identificar la región crítica. Los identificadores utilizados para identificar una región crítica tienen vinculación externa y se encuentran en un espacio de nombres que es independiente de los espacios de nombres utilizados por etiquetas, etiquetas, miembros y los identificadores normales.

Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso está ejecutando en una región crítica (en cualquier lugar en el programa) con el mismo nombre. Todo sin nombre **críticos** asignan directivas en el mismo nombre no especificado.