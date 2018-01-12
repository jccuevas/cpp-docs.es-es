---
title: Error del evaluador de expresiones CXX0064 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: CXX0064
dev_langs: C++
helpviewer_keywords:
- CAN0064
- CXX0064
ms.assetid: aa509e71-0616-41ca-a94e-6c376b041e57
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2edeb05e39c6d2e70cb2c9dde562a89e85921301
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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