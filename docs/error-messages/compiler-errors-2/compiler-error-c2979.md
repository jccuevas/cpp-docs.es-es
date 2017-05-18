---
title: Error del compilador C2979 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2979
dev_langs:
- C++
helpviewer_keywords:
- C2979
ms.assetid: 98bd9043-ec44-451e-a482-3a8e35fc7464
caps.latest.revision: 5
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
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 41fee13c594448132eab98eab4e9ec8f1ee6ee30
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2979"></a>Error del compilador C2979
no se admite especializaciones explícitas en genéricos  
  
 Se declaró una clase genérica incorrectamente.  Vea [genéricos](../../windows/generics-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2979.  
  
```  
// C2979.cpp  
// compile with: /clr /c  
generic <>   
ref class Utils {};   // C2979 error  
  
generic <class T>  
ref class Utils2 {};   // OK  
```
