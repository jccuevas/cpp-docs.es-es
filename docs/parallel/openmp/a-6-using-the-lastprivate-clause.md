---
title: A.6 usar la cláusula lastprivate | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 03d18d3aaf5c5d1cbe03282710ae4f4e2bb613f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390584"
---
# <a name="a6---using-the-lastprivate-clause"></a>A.6 Usar la cláusulas lastprivate

A veces, la ejecución correcta depende del valor que la última iteración de un bucle que se asigna a una variable. Estos programas deben enumerar todas las variables como argumentos a un `lastprivate` cláusula ([sección 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) en página 27) para que los valores de las variables son el mismo que cuando se ejecuta el bucle secuencial.

```
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

En el ejemplo anterior, el valor de `i` será igual al final de la región paralela `n-1`, como en el caso secuencial.