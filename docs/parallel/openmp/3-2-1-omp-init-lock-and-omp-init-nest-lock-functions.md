---
title: 3.2.1 funciones de omp_init_lock y omp_init_nest_lock | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 098a2721-b16a-484f-bc83-4b8e281e382c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3802822465d6527e4c98a0be6a8c274d767b0f52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="321-ompinitlock-and-ompinitnestlock-functions"></a>3.2.1 omp_init_lock y omp_init_nest_lock (Funciones)
Estas funciones proporcionan el único medio de inicializar un bloqueo. Cada función inicializa el bloqueo asociado al parámetro *bloqueo* para su uso en las llamadas subsiguientes. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
void omp_init_lock(omp_lock_t *lock);  
void omp_init_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El estado inicial está desbloqueado (es decir, no hay ningún subproceso posee el bloqueo). Un bloqueo anidable, el recuento de anidamiento inicial es cero. No es conforme al llamar a cualquiera de estas rutinas con una variable de bloqueo que ya se ha inicializado.