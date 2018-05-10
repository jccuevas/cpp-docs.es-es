---
title: 3.2.1 funciones de omp_init_lock y omp_init_nest_lock | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f14e182e6c981cd5de7a4cf92d8c285a4b49c66
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock (Funciones)
Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado al parámetro *bloqueo* para su uso en las llamadas subsiguientes. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El estado inicial está desbloqueado (es decir, no hay ningún subproceso posee el bloqueo). Un bloqueo anidable, el recuento de anidamiento inicial es cero. No es conforme al llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.