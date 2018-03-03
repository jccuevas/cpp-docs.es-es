---
title: "3.1.6 omp_in_parallel (función) | Documentos de Microsoft"
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
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e5d05af81eb112894ca27a7599c271138893ee1
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="316-ompinparallel-function"></a>3.1.6 omp_in_parallel (Función)
El **omp_in_parallel ()** función devuelve un valor distinto de cero si se llama dentro de la extensión dinámica de una región paralela en ejecución en paralelo; de lo contrario, devuelve 0. El formato es como se detalla a continuación:  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 Esta función devuelve un valor distinto de cero cuando se llama desde dentro de una región que se ejecutan en paralelo, incluidas las regiones anidadas que se serializan.