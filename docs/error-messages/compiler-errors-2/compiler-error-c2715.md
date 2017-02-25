---
title: "Error del compilador C2715 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2715"
ms.assetid: c81567a7-5b65-468f-aaf9-835f91e468e4
caps.latest.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# Error del compilador C2715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': no se puede aplicar throw ni catch a este tipo  
  
 Los tipos de valor no son argumentos válidos cuando se utiliza el control de excepciones en código administrado \(vea [Control de excepciones](../../windows/exception-handling-cpp-component-extensions.md) para obtener más información\).  
  
```  
// C2715a.cpp  
// compile with: /clr  
using namespace System;  
  
value struct V {  
   int i;  
};  
  
void f1() {  
   V v;  
   v.i = 10;  
   throw v;   // C2715  
   // try the following line instead  
   // throw ((V^)v);  
}  
  
int main() {  
   try {  
      f1();  
   }  
  
   catch(V v) { if ( v.i == 10 ) {   // C2715  
   // try the following line instead  
   // catch(V^ pv) { if ( pv->i == 10 ) {  
         Console::WriteLine("caught 10 - looks OK");  
      }   
      else {  
         Console::WriteLine("catch looks bad");  
      }  
   }  
   catch(...) {  
      Console::WriteLine("catch looks REALLY bad");  
   }  
}  
```  
  
 [Los tipos \_\_value](../../misc/value.md) o punteros [\_\_gc](../../misc/gc.md) no son argumentos válidos al usar el control de excepciones en las Extensiones administradas para C\+\+.  Para resolver este error, use la palabra clave [\_\_box](../../misc/box.md) para realizar así una operación 'boxing' en el argumento.  
  
 El código siguiente genera el error C2715:  
  
```  
// C2715b.cpp  
// compile with: /clr:oldSyntax  
using namespace System;  
  
__value struct V {  
   int i;  
};  
  
void f1() {  
   V v;  
   v.i = 10;  
   throw v;   // C2715  
   // try the following line instead  
   // throw __box(v);  
}  
  
int main() {  
   try {  
      f1();  
   }  
  
   catch(V v) { if ( v.i == 10 ) {   // C2715  
   // try the following line instead  
   // catch(__box V *pv) { if ( pv->i == 10 ) {  
         Console::WriteLine(S"caught 10 - looks OK");  
      }   
      else {  
         Console::WriteLine(S"catch looks bad");  
      }  
   }  
   catch(...) {  
      Console::WriteLine(S"catch looks REALLY bad");  
   }  
}  
```