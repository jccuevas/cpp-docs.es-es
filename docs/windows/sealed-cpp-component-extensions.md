---
title: "sealed (Extensiones de componentes de C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "sealed_cpp"
  - "sealed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sealed (palabra clave) [C++]"
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
caps.latest.revision: 26
caps.handback.revision: 24
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# sealed (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`sealed` es una palabra clave contextual para las clases ref que indica que no se puede reemplazar un miembro virtual o que no se puede usar un tipo como tipo base.  
  
> [!NOTE]
>  El lenguaje estándar ISO C \+\+ 11 tiene la palabra clave [final](../cpp/final-specifier.md), que es compatible con Visual Studio.  Use `final` en clases estándar y `sealed` en las clases ref.  
  
## Todos los runtimes  
 **Sintaxis**  
  
```  
  
ref class identifier sealed {...};  
virtual return-type identifier() sealed {...};  
  
```  
  
 **Parámetros**  
  
 *identificador*  
 Nombre de la función o clase.  
  
 *tipo de valor devuelto*  
 Tipo devuelto por una función.  
  
 **Comentarios**  
  
 En el primer ejemplo de sintaxis, una clase está sellada.  En el segundo ejemplo, una función virtual está sellada.  
  
 La palabra clave `sealed` es válida para destinos nativos, así como para [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] y Common Language Runtime \(CLR\).  Para obtener más información, consulte [Declarar especificadores de invalidación en las compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).  
  
 Puede detectar en tiempo de compilación si un tipo está sellado usando el rasgo de tipo `__is_sealed (``type``)`.  Para obtener más información, consulte [Compatibilidad de compilador para type traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 `sealed` es una palabra clave contextual.  Para obtener más información, consulte [Palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).  
  
## [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)]  
 Consulte [Ref \(Clases y structs\)](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx).  
  
### Requisitos  
 Opción del compilador: **\/ZW**  
  
## Common Language Runtime  
 \(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime\).  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 Este ejemplo de código siguiente muestra el efecto de `sealed` en un miembro virtual.  
  
```cpp  
// sealed_keyword.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
   virtual void g();  
};  
  
ref class X : I1 {  
public:  
   virtual void f() {  
      System::Console::WriteLine("X::f override of I1::f");  
   }  
  
   virtual void g() sealed {  
      System::Console::WriteLine("X::f override of I1::g");  
   }  
};  
  
ref class Y : public X {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("Y::f override of I1::f");  
   }  
  
   /*  
   // the following override generates a compiler error  
   virtual void g() override {  
      System::Console::WriteLine("Y::g override of I1::g");  
   }    
   */  
};  
  
int main() {  
   I1 ^ MyI = gcnew X;  
   MyI -> f();  
   MyI -> g();  
  
   I1 ^ MyI2 = gcnew Y;  
   MyI2 -> f();  
}  
```  
  
 **Resultado**  
  
  **Invalidación de X::f de I1::f**  
 **Invalidación de X::f de I1::g**  
 **Invalidación de Y::f de I1::f** En el ejemplo de código siguiente se muestra cómo marcar una clase como sellada.  
  
```cpp  
// sealed_keyword_2.cpp  
// compile with: /clr  
interface struct I1 {  
   virtual void f();  
};  
  
ref class X sealed : I1 {  
public:  
   virtual void f() override {}  
};  
  
ref class Y : public X {   // C3246 base class X is sealed  
public:  
   virtual void f() override {}  
};  
```  
  
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)