---
title: 2.6.1 master construcción | Microsoft Docs
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
ms.openlocfilehash: 8d82ae673e428c635172f35f9b0f682aa65dc2b8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445638"
---
# <a name="261-master-construct"></a>2.6.1 master (Construcción)

El **maestro** directiva identifica una construcción que especifica un bloque estructurado que se ejecuta el subproceso principal del equipo. La sintaxis de la **maestro** directiva es como sigue:

```
#pragma omp master new-linestructured-block
```

Otros subprocesos en el equipo no ejecuten el bloque estructurado asociado. No hay ninguna barrera implícita ya sea en la entrada o salida de la construcción principal.