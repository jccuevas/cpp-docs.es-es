---
title: C2798 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2798
dev_langs:
- C++
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: bb0a411651cf7c7f614942563baee5f04075fdf3
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2798"></a>C2798 de Error del compilador
'super:: miembro' es ambiguo  
  
 Varias estructuras heredadas que contienen el miembro al que hace referencia con [muy](../../cpp/super.md). Puede corregir el error, ya sea:  
  
-   Quitando B1 o B2 de la lista de herencia de D.  
  
-   Cambiar el nombre del miembro de datos en B1 o B2.  
  
 El ejemplo siguiente genera C2798:  
  
```  
// C2798.cpp  
struct B1 {  
   int i;  
};  
  
struct B2 {  
   int i;  
};  
  
struct D : B1, B2 {  
   void g() {  
      __super::i = 4; // C2798  
   }  
};  
```
