---
title: Compilador advertencia (nivel 2) C4396 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4396
dev_langs: C++
helpviewer_keywords: C4396
ms.assetid: 7cd6b283-db17-4574-b299-03e0b913ad70
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5bee2614d479ec54bf9d49c92deb336eee05d285
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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