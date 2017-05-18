---
title: Error del compilador C2978 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2978
dev_langs:
- C++
helpviewer_keywords:
- C2978
ms.assetid: 5e7bee82-e266-4ccd-ad2e-ee89606ec5bf
caps.latest.revision: 6
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
ms.openlocfilehash: e34fc28dd4b4bae71f2244e8539d69f1b775303c
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2978"></a>Error del compilador C2978
error de sintaxis: se esperaba 'palabraClave1' o 'palabraClave2'; se encontró el tipo 'palabraClave3'; no se admiten parámetros sin tipo en genéricos  
  
 Se declaró una clase genérica incorrectamente. Vea [genéricos](../../windows/generics-cpp-component-extensions.md)para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C2978.  
  
```  
// C2978.cpp  
// compile with: /clr /c  
generic <ref class T>   // C2978  
// try the following line instead  
// generic <typename T>   // OK  
ref class Utils {  
   static void sort(T elems, size_t size);  
};  
  
generic <int>  
// try the following line instead  
// generic <class T>  
ref class Utils2 {  
   static void sort(T elems, size_t size);  
};  
```
