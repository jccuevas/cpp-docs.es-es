---
title: Las herramientas del vinculador LNK2020 Error | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2020
dev_langs:
- C++
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33dd1b381d36a90f2e9b144e690e364ac512c081
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301962"
---
# <a name="linker-tools-error-lnk2020"></a>Error de las herramientas del vinculador LNK2020
símbolo (token) 'token' sin resolver  
  
 Es similar a un error externo no definido, excepto en que la referencia es a través de metadatos. En los metadatos, deben definirse todas las funciones y datos.  
  
 Para resolver:  
  
-   Definir la función que faltan o los datos, o  
  
-   Incluir el archivo objeto o biblioteca en la que la función o los datos que faltan ya está definidos.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error LNK2020.  
  
```  
// LNK2020.cpp  
// compile with: /clr /LD  
ref struct A {  
   A(int x);   // LNK2020  
   static int f();   // LNK2020  
};  
  
// OK  
ref struct B {  
   B(int x) {}  
   static int f() { return 0; }  
};  
```  
  
## <a name="example"></a>Ejemplo  
 También se producirá el error LNK2020 si se crea una variable de un tipo de plantilla administrado, pero no también crear instancias del tipo.  
  
 El ejemplo siguiente genera el error LNK2020.  
  
```  
// LNK2020_b.cpp  
// compile with: /clr   
  
template <typename T>  
ref struct Base {  
   virtual void f1() {};  
};  
  
template <typename T>  
ref struct Base2 {  
   virtual void f1() {};  
};  
  
int main() {  
   Base<int>^ p;   // LNK2020  
   Base2<int>^ p2 = gcnew Base2<int>();   // OK  
};  
```