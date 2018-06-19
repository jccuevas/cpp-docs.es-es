---
title: 3.1.10 omp_get_nested (función) | Documentos de Microsoft
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
ms.openlocfilehash: 7f447da6957cb385ace918120eb7ed7a5420e9f0
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686726"
---
# <a name="3110-ompgetnested-function"></a>3.1.10 omp_get_nested (Función)
El `omp_get_nested` función devuelve un valor distinto de cero si se habilita el paralelismo anidado y 0 si no lo está. Para obtener más información sobre paralelismo anidado, vea la sección 3.1.9 en la página 40. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 Si una implementación no implementa paralelismo anidado, esta función siempre devuelve 0.