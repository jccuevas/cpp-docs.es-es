---
title: "auto_gcroot::operator= | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "auto_gcroot.operator="
  - "msclr::auto_gcroot::operator="
  - "msclr.auto_gcroot.operator="
  - "auto_gcroot::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operator="
ms.assetid: 99eba5eb-5a2c-4edf-b3d5-c903f818233d
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# auto_gcroot::operator=
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Operador de asignación.  
  
## Sintaxis  
  
```  
auto_gcroot<_element_type> & operator=(  
   _element_type _right  
);  
auto_gcroot<_element_type> & operator=(  
   auto_gcroot<_element_type> & _right  
);  
template<typename _other_type>  
auto_gcroot<_element_type> & operator=(  
   auto_gcroot<_other_type> & _right  
);  
```  
  
#### Parámetros  
 `_right`  
 El objeto o `auto_gcroot` que se asignen a `auto_gcroot`actual.  
  
## Valor devuelto  
 `auto_gcroot`actual, ahora poseyendo `_right`.  
  
## Ejemplo  
  
```  
// msl_auto_gcroot_operator_equals.cpp  
// compile with: /clr  
#include <msclr\auto_gcroot.h>  
  
using namespace System;  
using namespace msclr;  
  
ref class ClassA {  
protected:  
   String^ m_s;     
public:  
   ClassA(String^ s) : m_s(s) {  
      Console::WriteLine( "in ClassA constructor: " + m_s );  
   }  
   ~ClassA() {  
      Console::WriteLine( "in ClassA destructor: " + m_s );  
   }  
  
   virtual void PrintHello() {  
      Console::WriteLine( "Hello from {0} A!", m_s );  
   }  
};  
  
ref class ClassB : ClassA {  
public:     
   ClassB( String^ s ) : ClassA( s ) {}  
   virtual void PrintHello() new {  
      Console::WriteLine( "Hello from {0} B!", m_s );  
   }  
};  
  
int main()  
{  
   auto_gcroot<ClassA^> a;  
   auto_gcroot<ClassA^> a2(gcnew ClassA( "first" ) );  
   a = a2; // assign from same type  
   a->PrintHello();  
  
   ClassA^ ha = gcnew ClassA( "second" );  
   a = ha; // assign from raw handle  
  
   auto_gcroot<ClassB^> b(gcnew ClassB( "third" ) );     
   b->PrintHello();  
   a = b; // assign from derived type     
   a->PrintHello();  
  
   Console::WriteLine("done");  
}  
```  
  
  **en el constructor de ClassA: primero**  
**¡Hola primero de A\!**  
**en el constructor de ClassA: en segundo lugar**  
**en ClassA destructor: primero**  
**en el constructor de ClassA: tercer**  
**¡Hola a partir de la tercera b\!**  
**en ClassA destructor: en segundo lugar**  
**¡Hola a partir de otros A\!**  
**done**  
**en ClassA destructor: tercer**   
## Requisitos  
 **Archivo de encabezado** \<msclr\\auto\_gcroot.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [auto\_gcroot \(Miembros\)](../dotnet/auto-gcroot-members.md)   
 [auto\_gcroot::attach](../dotnet/auto-gcroot-attach.md)