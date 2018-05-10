---
title: Uso A.30 de Reprivatization | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6026bba31fcc0db4e28ced14b3e847ac0cf8bf58
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="a30---use-of-reprivatization"></a>A.30 Uso de la reprivatización
En el ejemplo siguiente se muestra la reprivatization de variables. Se pueden marcar variables privadas `private` nuevo en una directiva anidada. No tiene que compartirse en la región paralela envolvente.  
  
```  
int i, a;  
...  
#pragma omp parallel private(a)  
{  
  ...  
  #pragma omp parallel for private(a)  
  for (i=0; i<10; i++)  
     {  
       ...  
     }  
}  
```