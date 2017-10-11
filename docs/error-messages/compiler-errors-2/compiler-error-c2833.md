---
title: Error del compilador C2833 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2833
dev_langs:
- C++
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 2d3adf42ddb4df4365a45fd3ef24bccd682ac3c9
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2833"></a>Error del compilador C2833
'operator operator' no es un operador o tipo reconocido  
  
 La palabra `operator` debe ir seguido de un operador que desea invalidar o un tipo que va a convertir.  
  
 Para obtener una lista de los operadores que se pueden definir en un tipo administrado, consulte [operadores definidos por el usuario](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 El ejemplo siguiente genera C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```
