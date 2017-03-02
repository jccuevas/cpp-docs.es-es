---
title: Error de compilador Error C2847 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2847
dev_langs:
- C++
helpviewer_keywords:
- C2847
ms.assetid: 9ad9a0e0-8b16-49d9-a5be-f8eda2372aa9
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c243063a9770542f137d5950e8a269f771960f74
ms.openlocfilehash: 004b3b4474593ac4350e35fd48309a271948a3ea
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2847"></a>Error del compilador C2847
no se puede aplicar sizeof al tipo administrado o WinRT 'class'  
  
 El [sizeof](../../cpp/sizeof-operator.md) operador obtiene el valor de un objeto en tiempo de compilación. El tamaño de un tipo de valor, una interfaz o una clase administrada o WinRT es dinámico y no puede conocerse en tiempo de compilación.  
  
 El ejemplo siguiente genera el error C2847:  
  
```  
// C2847.cpp  
// compile with: /clr  
ref class A {};  
  
int main() {  
   A ^ xA = gcnew A;  
   sizeof(*xA);   // C2847 cannot use sizeof on managed object  
}  
```  

