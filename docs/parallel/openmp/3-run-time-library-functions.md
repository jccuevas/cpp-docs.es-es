---
title: 3. Funciones de la biblioteca de tiempo de ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b226e512-6822-4cbe-a2ca-74cc2bb7e880
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d747f775509c6b3b2b95be51d95ea937816d3cd1
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688120"
---
# <a name="3-run-time-library-functions"></a>3. Funciones de la biblioteca de tiempo de ejecución
Esta sección describen las funciones de biblioteca en tiempo de ejecución de OpenMP C y C++. El encabezado  **\<omp.h >** declara dos tipos, varias funciones que pueden usarse para controlar y consultar el entorno de ejecución en paralelo y bloquear las funciones que pueden utilizarse para sincronizar el acceso a datos.  
  
 El tipo **omp_lock_t** es un tipo de objeto puede representar que un bloqueo está disponible, o que un subproceso posee un bloqueo. Estos bloqueos se conocen como *bloqueos simples*.  
  
 El tipo **omp_nest_lock_t** es un tipo de objeto puede representar que un bloqueo está disponible o la identidad del subproceso que posee el bloqueo y una *anidar recuento* (descritos a continuación). Estos bloqueos se conocen como *anidable bloqueos*.  
  
 Las funciones de biblioteca son funciones externas con vinculación de "C".  
  
 Las descripciones en este capítulo se dividen en los siguientes temas:  
  
-   Funciones de entorno de ejecución (vea [sección 3.1](../../parallel/openmp/3-1-execution-environment-functions.md) en página 35).  
  
-   Funciones de bloqueo (vea [sección 3.2](../../parallel/openmp/3-2-lock-functions.md) en la página 41).