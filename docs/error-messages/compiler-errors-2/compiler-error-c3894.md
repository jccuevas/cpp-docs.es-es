---
title: "Error del compilador C3894 | Microsoft Docs"
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
  - "C3894"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3894"
ms.assetid: 6d5ac903-1dea-431d-8e3a-cebca4342983
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3894
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'variable': el uso del valor L del miembro de datos estático initonly solamente se permite en el constructor de clase de la clase 'clase'  
  
 Los miembros de datos [initonly](../../dotnet/initonly-cpp-cli.md) estáticos sólo se pueden utilizar como valores L en su punto de declaración o en un constructor estático.  
  
 Los miembros de datos initonly \(no estáticos\) de instancias sólo se pueden utilizar como valores L en su punto de declaración o en constructores \(no estáticos\) de instancias.  
  
 El código siguiente genera el error C3894:  
  
```  
// C3894.cpp  
// compile with: /clr  
ref struct Y1 {  
   initonly static int data_var = 0;  
  
public:  
   // class constructor  
   static Y1() {  
      data_var = 99;   // OK  
      System::Console::WriteLine("in static constructor");  
   }  
  
   // not the class constructor  
   Y1(int i) {  
      data_var = i;   // C3894  
   }  
  
   static void Test() {}  
  
};  
  
int main() {  
   Y1::data_var = 88;   // C3894  
   int i = Y1::data_var;  
   Y1 ^ MyY1 = gcnew Y1(99);  
   Y1::Test();  
}  
```