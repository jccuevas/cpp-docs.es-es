---
title: "Error del compilador C3225 | Microsoft Docs"
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
  - "C3225"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3225"
ms.assetid: f5f66973-256e-4298-ac46-c87819cbde34
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3225
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el argumento de tipo genérico para 'arg' no puede ser 'tipo', debe ser un tipo de valor o un tipo de identificador  
  
 El argumento de tipo genérico no es del tipo correcto.  
  
 Para obtener más información, vea [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 No puede crear instancias de un tipo genérico con un tipo nativo.  El ejemplo siguiente genera el error C3225.  
  
```  
// C3225.cpp  
// compile with: /clr  
class A {};  
  
ref class B {};  
  
generic <class T>  
ref class C {};  
  
int main() {  
   C<A>^ c = gcnew C<A>;   // C3225  
   C<B^>^ c2 = gcnew C<B^>;   // OK  
}  
```  
  
## Ejemplo  
 El siguiente ejemplo crea un componente utilizando C\#.  Observe que la restricción especifica que sólo se pueden crear instancias del tipo genérico con un tipo de valor.  
  
```  
// C3225_b.cs  
// compile with: /target:library  
// a C# program  
public class MyList<T> where T: struct {}  
```  
  
## Ejemplo  
 Este ejemplo utiliza el componente creado en C\# e infringe la restricción de que sólo se pueden crear instancias de MyList con un tipo de valor distinto de <xref:System.Nullable>.  El ejemplo siguiente genera el error C3225.  
  
```  
// C3225_c.cpp  
// compile with: /clr  
#using "C3225_b.dll"  
ref class A {};  
value class B {};  
int main() {  
   MyList<A> x;   // C3225  
   MyList<B> y;   // OK  
}  
```