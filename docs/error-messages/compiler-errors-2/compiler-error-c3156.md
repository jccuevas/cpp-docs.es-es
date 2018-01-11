---
title: Error de compilador el error C3156 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3156
dev_langs: C++
helpviewer_keywords: C3156
ms.assetid: 1876da78-b94e-4af7-9795-28f72b209b3e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4f6bfb5e9af810d9126617e960a7da6d98d6fab4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3156"></a>Error C3156 de Error de compilador
'class' : no se puede tener una definición local de un tipo administrado o WinRT  
  
 Una función no puede contener la definición o la declaración de un struct, una interfaz o una clase administrada o WinRT.  
  
## <a name="example"></a>Ejemplo  
 El siguiente ejemplo genera el error C3156.  
  
```  
// C3156.cpp  
// compile with: /clr /c  
void f() {  
   ref class X {};   // C3156  
   ref class Y;   // C3156  
}  
```  
