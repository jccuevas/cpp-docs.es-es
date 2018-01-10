---
title: Error del compilador C3920 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3920
dev_langs: C++
helpviewer_keywords: C3920
ms.assetid: 66e91f28-ed82-4ce2-bf22-c0c74905b1ed
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b5eeee973258b6d59b7a034e2b71bc453ed7454f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3920"></a>Error del compilador C3920
' operador '': no se puede definir un operador CLR postfijo de llamada o incremento y decremento WinRT operador WinRT o CLR llamará prefijo correspondiente WinRT o CLR operador (op_Increment/op_Decrement), pero con semántica de postfijo  
  
 Windows Runtime y CLR no admiten el operador de postfijo y no se permiten los operadores de postfijo definidos por el usuario.  Puede definir un operador de prefijo que se usará para ambas operaciones de incremento previo y posterior.  
  
 El ejemplo siguiente genera el error C3920 y muestra cómo corregirlo:  
  
```  
// C3920.cpp  
// compile with: /clr /LD  
public value struct V {  
   static V operator ++(V me, int)  
   // try the following line instead  
   // static V operator ++(V me)  
   {   // C3920  
      me.m_i++;  
      return me;  
   }  
  
   int m_i;  
};  
  
```