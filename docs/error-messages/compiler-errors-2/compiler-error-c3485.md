---
title: Error del compilador C3485 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3485
dev_langs: C++
helpviewer_keywords: C3485
ms.assetid: d67536f9-67a1-4ad9-9a94-d8bbbca3d0dc
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cd49b93beb54776bf17a9ee2bc5c9816f0964451
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3485"></a>Error del compilador C3485
una definición de lambda no puede tener ningún calificador cv  
  
 No puede usar un calificador `const` o `volatile` como parte de la definición de una expresión lambda.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite el calificador `const` o `volatile` de la definición de la expresión lambda.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3485 porque usa el calificador `const` como parte de la definición de una expresión lambda:  
  
```  
// C3485.cpp  
  
int main()  
{  
   auto x = []() const mutable {}; // C3485  
}  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones lambda](../../cpp/lambda-expressions-in-cpp.md)