---
title: "C&#243;mo: Declarar tipos de valor con la palabra clave interior_ptr (C++/CLI) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_ptr (palabra clave)"
  - "tipos de valor, declarar"
ms.assetid: 49eea66e-eeba-49bd-95b0-ba297be436e3
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C&#243;mo: Declarar tipos de valor con la palabra clave interior_ptr (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`interior_ptr` se puede utilizar con un tipo de valor.  
  
> [!IMPORTANT]
>  Esta característica de lenguaje es compatible con la opción del compilador **\/clr** , pero no por la opción del compilador **\/ZW** .  
  
## Ejemplo  
  
### Descripción  
 El siguiente ejemplo de [!INCLUDE[cppcli](../build/reference/includes/cppcli_md.md)] muestra cómo utilizar `interior_ptr` con un tipo de valor.  
  
### Código  
  
```  
// interior_ptr_value_types.cpp  
// compile with: /clr  
value struct V {  
   V(int i) : data(i){}  
   int data;  
};  
  
int main() {  
   V v(1);  
   System::Console::WriteLine(v.data);  
  
   // pointing to a value type  
   interior_ptr<V> pv = &v;  
   pv->data = 2;  
  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
  
   // pointing into a value type  
   interior_ptr<int> pi = &v.data;  
   *pi = 3;  
   System::Console::WriteLine(*pi);  
   System::Console::WriteLine(v.data);  
   System::Console::WriteLine(pv->data);  
}  
```  
  
### Resultados  
  
```  
1  
2  
2  
3  
3  
3  
```  
  
## Ejemplo  
  
### Descripción  
 En un tipo de valor, el puntero de `this` evalúa un interior\_ptr.  
  
 En el cuerpo de una miembro\- función no estática de un tipo de valor `V`, `this` es una expresión de `interior_ptr<V>` tipo cuyo valor es la dirección del objeto para el que se llama a la función.  
  
### Código  
  
```  
// interior_ptr_value_types_this.cpp  
// compile with: /clr /LD  
value struct V {  
   int data;  
   void f() {  
      interior_ptr<V> pv1 = this;  
      // V* pv2 = this;   error  
   }  
};  
```  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente se muestra cómo utilizar el dirección\- de operator con miembros estáticos.  
  
 La dirección de un miembro de tipo Visual C\+\+ de estático produce un puntero nativo.  La dirección de un miembro estático del tipo de valor es un puntero administrado porque asignan en el montón en tiempo de ejecución y se puede desplazar el miembro de tipo de valor por el recolector de elementos no utilizados.  
  
### Código  
  
```  
// interior_ptr_value_static.cpp  
// compile with: /clr  
using namespace System;  
value struct V { int i; };  
  
ref struct G {  
   static V v = {22};   
   static int i = 23;   
   static String^ pS = "hello";   
};  
  
int main() {  
   interior_ptr<int> p1 = &G::v.i;  
   Console::WriteLine(*p1);  
  
   interior_ptr<int> p2 = &G::i;  
   Console::WriteLine(*p2);  
  
   interior_ptr<String^> p3 = &G::pS;  
   Console::WriteLine(*p3);  
}  
```  
  
### Resultados  
  
```  
22  
23  
hello  
```  
  
## Vea también  
 [interior\_ptr \(C\+\+\/CLI\)](../windows/interior-ptr-cpp-cli.md)