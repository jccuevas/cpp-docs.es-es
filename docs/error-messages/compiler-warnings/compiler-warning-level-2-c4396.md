---
title: Compilador advertencia (nivel 2) C4396 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4396
dev_langs:
- C++
helpviewer_keywords:
- C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: 11
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
translationtype: Machine Translation
ms.sourcegitcommit: 84f0628de933344eb23dc6325679abdcd3699c3a
ms.openlocfilehash: 8e0538cc5a1ec9279c4d84cb9e23e0d6fabfd77e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-2-c4396"></a>Advertencia del compilador (nivel 2) C4396
"name": el especificador inline no se puede usar cuando una declaración de confianza hace referencia a una especialización de una plantilla de función  
  
 Una especialización de una plantilla de función no puede especificar cualquiera de los [en línea](../../cpp/inline-functions-cpp.md) especificadores. El compilador emite la advertencia C4396 y omite el especificador inline.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Quite el especificador `inline`, `__inline`o `__forceinline` de la declaración de función friend.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo de código siguiente muestra una declaración de función friend no válida con un especificador `inline` .  
  
```  
// C4396.cpp  
// compile with: /W2 /c  
  
class X;   
template<class T> void Func(T t, int i);  
  
class X {  
    friend inline void Func<char>(char t, int i);  //C4396  
// try the following line instead  
//    friend void Func<char>(char t, int i);   
    int i;  
};  
```
