---
title: "Invalidaciones expl&#237;citas (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
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
  - "reemplazar, invalidación [C++]"
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
caps.latest.revision: 21
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Invalidaciones expl&#237;citas (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo reemplazar explícitamente un miembro de una clase base o interfaz.  Un reemplazo \(explícita\) denominada sólo se debe utilizar para invalidar un método con un método derivado con un nombre diferente.  
  
## Todos los runtimes  
 **Sintaxis**  
  
```  
  
        overriding-function-declarator = type::function [,type::function] { overriding-function-definition }  
overriding-function-declarator = function { overriding-function-definition }  
```  
  
 **Parámetros**  
  
 *overriding\-function\-declarator*  
 El tipo de valor devuelto, el nombre, y la lista de argumentos de la función de reemplazo.  Observe que la función de reemplazo no tiene que tener el mismo nombre que la función que se reemplaza.  
  
 *type*  
 El tipo base que contiene una función replace.  
  
 *function*  
 Una lista delimitada por comas de uno o más nombres de función a reemplazar.  
  
 *overriding\-function\-definition*  
 Las instrucciones del cuerpo de la función que definen la función de reemplazo.  
  
 **Comentarios**  
  
 El uso explícito reemplaza para crear un alias para una firma de método, o proporcionar implementaciones diferentes para los métodos con la misma firma.  
  
 Para obtener información sobre la modificación del comportamiento de tipos heredados y miembros de tipo heredados, vea [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md).  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 Para obtener información sobre explícita reemplaza en código nativo o código compilado con **\/clr:oldSyntax**, vea [Invalidaciones explícitas](../cpp/explicit-overrides-cpp.md).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 El ejemplo de código siguiente muestra un reemplazo simple, implícita y la implementación de un miembro en una interfaz base, no con explícita reemplaza.  
  
```  
// explicit_override_1.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
}  
```  
  
 **Resultados**  
  
  **Invalidación X::f de I1::f** **Ejemplo**  
  
 El siguiente ejemplo de código muestra cómo implementar todos los miembros de la interfaz con una firma común, utilizando la sintaxis de reemplazo explícita.  
  
```  
  
// explicit_override_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
interface struct I2 {  
   virtual void f();  
};  
  
ref struct X : public I1, I2 {  
   virtual void f() = I1::f, I2::f {  
      System::Console::WriteLine("X::f override of I1::f and I2::f");  
   }  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   I2 ^ MyI2 = gcnew X;  
   MyI -> f();  
   MyI2 -> f();  
}  
```  
  
 **Resultados**  
  
  **Reemplazo de X::f de I1::f y de I2::f**  
 **Reemplazo de X::f de I1::f y de I2::f** **Ejemplo**  
  
 El ejemplo de código siguiente muestra cómo un reemplazo de la función puede tener un nombre diferente de la función que implementa.  
  
```  
// explicit_override_3.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X : public I1 {  
public:  
   virtual void g() = I1::f {  
      System::Console::WriteLine("X::g");  
   }  
};  
  
int main() {  
   I1 ^ a = gcnew X;  
   a->f();  
}  
```  
  
 **Resultados**  
  
  **X::g** **Ejemplo**  
  
 El ejemplo de código siguiente se muestra una implementación de interfaz explícita que implemente una colección seguros de tipo.  
  
```  
// explicit_override_4.cpp  
// compile with: /clr /LD  
using namespace System;  
ref class R : ICloneable {  
   int X;  
  
   virtual Object^ C() sealed = ICloneable::Clone {  
      return this->Clone();  
   }  
  
public:  
   R() : X(0) {}  
   R(int x) : X(x) {}  
  
   virtual R^ Clone() {  
      R^ r = gcnew R;  
      r->X = this->X;  
      return r;  
   }  
};  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)