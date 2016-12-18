---
title: "Error del compilador C3162 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3162"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3162"
ms.assetid: 0d4c4a24-1456-4191-b7d8-c38cb7b17c32
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3162
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo' : un tipo de referencia con destructor no se puede utilizar como tipo de miembro de datos estático 'miembro'  
  
 Common Language Runtime no puede saber cuándo ejecutar un destructor definido por el usuario si la clase también contiene una función miembro estática.  
  
 Un destructor no se ejecutará nunca, salvo que el objeto se elimine explícitamente.  
  
 Para obtener más información, vea  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Problemas comunes de migración a 64 bits en Visual C\+\+](../../build/common-visual-cpp-64-bit-migration-issues.md)  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3162.  
  
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