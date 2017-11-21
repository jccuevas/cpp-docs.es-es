---
title: 3.2.5 omp_test_lock y omp_test_nest_lock funciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 36818945-c22c-4c24-b754-4e73eba6f3f8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa340ce56d0e669a40b131a4cb3efbe18fc3c430
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="325-omptestlock-and-omptestnestlock-functions"></a>3.2.5 omp_test_lock y omp_test_nest_lock (Funciones)
Estas funciones se intentan establecer un bloqueo, pero no impiden la ejecución del subproceso. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_test_lock(omp_lock_t *lock);  
int omp_test_nest_lock(omp_nest_lock_t *lock);  
```  
  
 El argumento debe apuntar a una variable de bloqueo inicializado. Estas funciones se intentan establecer un bloqueo de la misma manera que `omp_set_lock` y `omp_set_nest_lock`, salvo que no bloqueen la ejecución del subproceso.  
  
 Un bloqueo simple, la `omp_test_lock` función devuelve un valor distinto de cero si el bloqueo se estableció correctamente; en caso contrario, devuelve cero.  
  
 Un bloqueo anidable, la `omp_test_nest_lock` función devuelve el recuento de anidamiento de nuevo si el bloqueo se estableció correctamente; en caso contrario, devuelve cero.