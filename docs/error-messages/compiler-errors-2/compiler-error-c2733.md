---
title: C2733 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2733
dev_langs:
- C++
helpviewer_keywords:
- C2733
ms.assetid: 67f83561-c633-407c-a2ee-f9fd16e165bf
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: fb0c21850d93a39047bacfe38592e381e9fb5918
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2733"></a>C2733 de Error del compilador
segunda vinculación C de la función sobrecargada 'función' no permitida  
  
 Más de una función sobrecargada se declara con una vinculación C. Al utilizar la vinculación de C, un único formato de una función especificada puede ser externo. Dado que las funciones sobrecargadas tienen el mismo nombre no representativo, que no pueden utilizarse con los programas de C.  
  
 El ejemplo siguiente genera C2733:  
  
```  
// C2733.cpp  
extern "C" {  
   void F1(int);  
}  
  
extern "C" {  
   void F1();   // C2733  
   // try the following line instead  
   // void F2();  
}  
```