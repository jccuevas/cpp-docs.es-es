---
title: "Error del compilador C3824 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3824"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3824"
ms.assetid: b6c6adf1-0a29-401c-a06e-616fd50d4c37
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C3824
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'miembro': este tipo no puede aparecer en este contexto \(parámetro de función, tipo de valor devuelto o miembro estático\)  
  
 Los punteros anclados no pueden ser parámetros de función, tipos de valor devueltos ni declarados como `static`.  
  
 El código siguiente genera el error C3824:  
  
```  
// C3824a.cpp  
// compile with: /clr /c  
void func() {  
   static pin_ptr<int> a; // C3824  
   pin_ptr<int> b; // OK  
}  
```  
  
 **Extensiones administradas de C\+\+**  
  
 Los punteros locales declarados con la palabra clave `__pin` no se pueden declarar como `static` ni ser punteros interiores.  
  
 El código siguiente genera el error C3824:  
  
```  
// C3824b.cpp  
// compile with: /clr:oldSyntax /c  
#using <mscorlib.dll>  
  
__gc struct A {};  
  
void func() {  
   static A __pin* a;   // C3824  
   A __pin* b;   // OK  
}  
```