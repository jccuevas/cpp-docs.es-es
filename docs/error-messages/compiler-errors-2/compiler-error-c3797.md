---
title: Error del compilador C3797 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3797
dev_langs:
- C++
helpviewer_keywords:
- C3797
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 231db7e59eab4e59b4b51d113db431fc484c5fb3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3797"></a>Error del compilador C3797
'override': declaración de evento no puede tener el especificador de invalidación (en su lugar se debe colocar en métodos add, remove y raise)  
  
 No se puede reemplazar un evento trivial (un evento sin métodos de descriptor de acceso definidos explícitamente) con otro evento trivial. El evento que reemplaza debe definir su comportamiento con funciones de descriptor de acceso.  
  
 Para obtener más información, consulte [eventos](../../windows/event-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3797.  
  
```  
// C3797.cpp  
// compile with: /clr /c  
delegate void MyDel();  
  
ref class Class1 {  
public:  
   virtual event MyDel ^ E;  
};  
  
ref class Class2 : public Class1 {  
public:  
   virtual event MyDel ^ E override;   // C3797  
};  
  
// OK  
ref class Class3 : public Class1 {  
public:  
   virtual event MyDel ^ E {  
      void add(MyDel ^ d) override {}  
      void remove(MyDel ^ d) override {}  
   }  
};  
```