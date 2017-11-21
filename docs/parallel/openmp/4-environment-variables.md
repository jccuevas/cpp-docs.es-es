---
title: 4. Las Variables de entorno | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5fcd308f21d66535a983e70506fe91afb5c7042f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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