---
title: 4. Las Variables de entorno | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: edd4f795a3511358d2b95b93e180b9b21b964dd2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="4-environment-variables"></a>4. Variables de entorno
Este capítulo describen las variables de entorno de OpenMP C y C++ API (o equivalente mecanismos específicos de la plataforma) que controlan la ejecución de código paralelo.  Los nombres de variables de entorno deben estar en mayúsculas. Los valores asignados a ellos distinguen mayúsculas de minúsculas y pueden tener espacios en blanco iniciales y finales.  Se omiten las modificaciones realizadas en los valores después de que ha iniciado el programa.  
  
 Las variables de entorno son los siguientes:  
  
-   **OMP_SCHEDULE** establece el tamaño de tipo y el fragmento de la programación de tiempo de ejecución.  
  
-   **OMP_NUM_THREADS** establece el número de subprocesos que se utilizarán durante la ejecución.  
  
-   **OMP_DYNAMIC** habilita o deshabilita el ajuste dinámico del número de subprocesos.  
  
-   **OMP_NESTED** habilita o deshabilita el paralelismo anidado.  
  
 Los ejemplos de este capítulo solo muestran cómo se podrían establecer estas variables en entornos de shell (csh) de C Unix. En Korn shell y entornos de DOS de las acciones son similares, como se indica a continuación:  
  
 csh:  
 setenv OMP_SCHEDULE "dinámico"  
  
 ksh:  
 Exportar OMP_SCHEDULE = "dinámico"  
  
 DOS:  
 establecer OMP_SCHEDULE = "dinámico"