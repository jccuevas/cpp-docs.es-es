---
title: 4. Las Variables de entorno | Microsoft Docs
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
ms.openlocfilehash: aec56dad334dcd27de2068e660ff8ec5a6e72f90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415503"
---
# <a name="4-environment-variables"></a>4. Variables de entorno

Este capítulo describe las variables de entorno de OpenMP C y C++ API (o equivalente mecanismos específicos de la plataforma) que controlan la ejecución de código paralelo.  Los nombres de variables de entorno deben estar en mayúsculas. Los valores asignados a ellos distinguen mayúsculas de minúsculas y pueden tener espacios en blanco iniciales y finales.  Se omiten las modificaciones en los valores de una vez iniciado el programa.

Las variables de entorno son los siguientes:

- **OMP_SCHEDULE** establece el tamaño de tipo y el fragmento de la programación de tiempo de ejecución.

- **OMP_NUM_THREADS** establece el número de subprocesos que se utilizarán durante la ejecución.

- **OMP_DYNAMIC** habilita o deshabilita el ajuste dinámico del número de subprocesos.

- **OMP_NESTED** habilita o deshabilita el paralelismo anidado.

Los ejemplos de este capítulo solo muestran cómo se pueden establecer estas variables en entornos de shell (csh) de C Unix. En Korn shell y entornos de DOS de las acciones son similares, como sigue:

csh: setenv OMP_SCHEDULE "dinámico"

ksh: exportar OMP_SCHEDULE = "dinámico"

Denegación de servicio: establecer OMP_SCHEDULE = "dinámico"