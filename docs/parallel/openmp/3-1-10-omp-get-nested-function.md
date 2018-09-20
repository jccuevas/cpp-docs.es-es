---
title: 3.1.10 omp_get_nested (función) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d019dd757080bbc87ff7aaab1a8745b2a3156b39
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392286"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested (Función)

El `omp_get_nested` función devuelve un valor distinto de cero si se habilita el paralelismo anidado y 0 si no lo está. Para obtener más información sobre el paralelismo anidado, vea la sección 3.1.9 en la página 40. El formato es como se detalla a continuación:

```
#include <omp.h>
int omp_get_nested(void);
```

Si una implementación no implementa paralelismo anidado, esta función siempre devuelve 0.