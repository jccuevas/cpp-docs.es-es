---
title: Error del compilador C3290 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3290
dev_langs: C++
helpviewer_keywords: C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 28f350f8cf522032fbdaad22098508ec8545ee01
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3290"></a>Error del compilador C3290
'type': una propiedad trivial no puede tener tipo de referencia  
  
 Se ha declarado incorrectamente una propiedad. Cuando se declara una propiedad trivial, el compilador crea una variable que actualizará la propiedad y no es posible tener una variable de referencia de seguimiento en una clase.  
  
 Vea [propiedad](../../windows/property-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md) para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3290.  
  
```  
// C3290.cpp  
// compile with: /clr /c  
ref struct R {};  
  
ref struct X {  
   R^ mr;  
  
   property R % y;   // C3290  
   property R ^ x;   // OK  
  
   // OK  
   property R% prop {  
      R% get() {   
         return *mr;   
      }  
  
      void set(R%) {}  
   }  
};  
  
int main() {  
   X x;  
   R% xp = x.prop;  
}  
```