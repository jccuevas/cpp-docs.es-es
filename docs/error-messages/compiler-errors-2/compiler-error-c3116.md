---
title: Error del compilador C3116 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3116
dev_langs:
- C++
helpviewer_keywords:
- C3116
ms.assetid: 597463e1-a5cc-4ed3-a917-eae9a61d3312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fde589df31e6e3b75f9a0153d7383ab1e85ed180
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3116"></a>Error del compilador C3116
'especificador de almacenamiento': clase de almacenamiento no es válida para el método de interfaz  
  
 Se utiliza `typedef`, `register`, o `static` como la clase de almacenamiento para un método de interfaz. Estas clases de almacenamiento no se permiten en los miembros de interfaz.  
  
 El ejemplo siguiente genera C3116:  
  
```  
// C3116.cpp  
__interface ImyInterface  
{  
   static void myFunc();   // C3116  
};  
```