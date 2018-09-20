---
title: 2.6.6 ordered (construcción) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 5b3c1ba5-cfb8-4b05-865b-f446ae1c9f7c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b83c3dfc13b231a1314343a1dff496acf7a99b6
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46412202"
---
# <a name="266-ordered-construct"></a>2.6.6 ordered (Construcción)

El bloque estructurado que sigue un **ordenados** directiva se ejecuta en el orden en el que se ejecutan en un bucle secuencial iteraciones. La sintaxis de la **ordenados** directiva es como sigue:

```
#pragma omp ordered new-linestructured-block
```

Un **ordenados** directiva debe estar dentro de la extensión dinámica de un **para** o **paralelas para** construir. El **para** o **paralelas para** la directiva a la que el **ordenados** construcción enlaza debe tener un **ordenados** cláusula especificada como se describe en [Sección 2.4.1](../../parallel/openmp/2-4-1-for-construct.md) en página 11. En la ejecución de un **para** o **paralelas para** construir con un **ordenados** cláusula, **ordenados** construcciones se ejecutan de forma estricta en el orden en el que se ejecutaría en una ejecución secuencial del bucle.

Restricciones para el **ordenados** directiva son los siguientes:

- Una iteración de un bucle con un **para** construcción no debe ejecutar la misma directiva ordered más de una vez y no debe ejecutar más de un **ordenados** directiva.