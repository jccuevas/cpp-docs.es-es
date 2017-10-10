---
title: Error del compilador C2951 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2951
dev_langs:
- C++
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4be1b3a298fc24572fcc44b9deb031c0d49b7332
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c2951"></a>Error del compilador C2951
solo se permiten en el espacio de nombres global, las declaraciones de tipo o ámbito de clase  
  
 No se puede declarar una clase genérica o clase de plantilla fuera global o ámbito de espacio de nombres. Si hace que las declaraciones de clase genérica o plantilla en un archivo de inclusión, asegúrese de que el archivo de inclusión está en el ámbito global.  
  
 El ejemplo siguiente genera C2951:  
  
```  
// C2951.cpp  
template <class T>  
class A {};  
  
int main() {  
   template <class T>   // C2951  
   class B {};  
}  
```  
  
 C2951 también puede producirse al usar genéricos:  
  
```  
// C2951b.cpp  
// compile with: /clr /c  
  
// OK  
generic <class T>   
ref class GC { };  
  
int main() {  
   generic <class T> ref class GC2 {};   // C2951  
}  
```
