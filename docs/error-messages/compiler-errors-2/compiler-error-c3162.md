---
title: Error del compilador C3162 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3162
dev_langs:
- C++
helpviewer_keywords:
- C3162
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 8bfde260ef0efe58ed70469a80a8bf7316eefa46
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3162"></a>Error del compilador C3162
'type': un tipo de referencia que tiene un destructor no se puede usar como el tipo de miembro de datos estático 'miembro'  
  
 Common language runtime no puede saber cuándo se debe ejecutar un destructor definido por el usuario cuando la clase también contiene una función miembro static.  
  
 Un destructor nunca se ejecutará a menos que el objeto se elimina de forma explícita.  
  
 Para obtener más información, vea  
  
-   [/CLR (compilación de common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C++](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3162.  
  
```  
// C3162.cpp  
// compile with: /clr /c  
ref struct A {  
   ~A() { System::Console::WriteLine("in destructor"); }  
   static A i;   // C3162  
   static A^ a = gcnew A;   // OK  
};  
  
int main() {  
   A ^ a = gcnew A;  
   delete a;  
}  
```
