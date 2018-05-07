---
title: Error del evaluador de expresiones CXX0064 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0064
dev_langs:
- C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7964eac628fa89695d1757cff8b7b329fd7fe713
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="expression-evaluator-error-cxx0064"></a>Error del evaluador de expresiones CXX0064
no se puede establecer un punto de interrupción en la función miembro virtual enlazada  
  
 Un punto de interrupción se estableció en una función miembro virtual a través de un puntero a un objeto, como:  
  
```  
pClass->vfunc( int );  
```  
  
 Un punto de interrupción se puede establecer en una función virtual escribiendo la clase, como:  
  
```  
Class::vfunc( int );  
```  
  
 Este error es idéntico a CAN0064.