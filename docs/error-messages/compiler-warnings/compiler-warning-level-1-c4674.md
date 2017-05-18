---
title: Compilador advertencia (nivel 1) C4674 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: ca99a22e6f91f44af58a1421d59151597017cddb
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4674"></a>Advertencia del compilador (nivel 1) C4674
'method' se debe declarar como 'static' y tener exactamente un parámetro  
  
La firma de un operador de conversión no es correcta. El método no se considera una conversión definida por el usuario. Para obtener más información sobre la definición de operadores, vea [operadores definidos por el usuario (C++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md) y [conversiones definidas por el usuario (C++ / CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4674.  
  
```  
// C4674.cpp  
// compile with: /clr /WX /W1 /LD  
ref class G {  
   int op_Implicit(int i) {   // C4674  
      return 0;  
   }  
};  
```  

