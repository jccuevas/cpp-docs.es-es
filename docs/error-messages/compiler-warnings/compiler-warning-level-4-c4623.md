---
title: "Advertencia del compilador (nivel 4) C4623 | Microsoft Docs"
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
  - "C4623"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4623"
ms.assetid: e630d8d0-f6ea-469c-a74f-07b027587225
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4623
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'`derived class`': El constructor predeterminado se definió implícitamente como eliminado porque un constructor predeterminado de clase base es inaccesible o se eliminó  
  
 Un constructor no estaba accesible en una clase base y no se generó para la clase derivada.  Cualquier intento de crear un objeto de este tipo en la pila provocará un error del compilador.  
  
 De forma predeterminada, esta advertencia está desactivada.  Consulte [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para obtener más información.  
  
## Ejemplo  
 El ejemplo siguiente genera C4623:  
  
```  
// C4623.cpp  
// compile with: /W4  
#pragma warning(default : 4623)  
class B {  
   B();  
};  
  
class C {  
public:  
   C();  
};  
  
class D : public B {};   // C4623 - to fix, make B's constructor public  
class E : public C {};   // OK - class C constructor is public  
  
int main() {  
   // D d;  will cause an error  
}  
```