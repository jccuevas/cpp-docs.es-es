---
title: "new (nueva ranura en vtable) (Extensiones de componentes de C++) | Microsoft Docs"
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
  - "new (palabra clave) [C++]"
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
caps.latest.revision: 20
caps.handback.revision: 18
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# new (nueva ranura en vtable) (Extensiones de componentes de C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La palabra clave `new` indica que un miembro virtual obtendrá una nueva ranura en vtable.  
  
> [!NOTE]
>  La palabra clave `new` tiene muchos usos y significados.  Para obtener más información, vea el tema sobre eliminación de ambigüedades [new](../misc/new.md).  
  
## Todos los runtimes  
 \(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.\)  
  
## Windows en tiempo de ejecución  
 No se admite en la [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)].  
  
## [!INCLUDE[clr_for_headings](../dotnet/includes/clr_for_headings_md.md)]  
 **Comentarios**  
  
 En una compilación **\/clr**, `new` indica que un miembro virtual obtendrá una nueva ranura en vtable; que la función no reemplaza un método de clase base.  
  
 `new` hace que el modificador newslot se agregue al IL para la función.  Para obtener más información sobre newslot, vea:  
  
-   [\<caps:sentence id\="tgt11" sentenceid\="e9bb59a12f97840a5c3173bb77c6b5b1" class\="tgtSentence"\>Método MethodInfo.GetBaseDefinition\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [\<caps:sentence id\="tgt12" sentenceid\="f6ceddd85a425f38e7ed06e94a9808a9" class\="tgtSentence"\>Enumeración MethodAttributes\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### Requisitos  
 Opción del compilador: **\/clr**  
  
### Ejemplos  
 **Ejemplo**  
  
 En el siguiente ejemplo se muestra el efecto de `new`.  
  
```  
// newslot.cpp  
// compile with: /clr  
ref class C {  
public:  
   virtual void f() {  
      System::Console::WriteLine("C::f() called");  
   }  
  
   virtual void g() {  
      System::Console::WriteLine("C::g() called");  
   }  
};  
  
ref class D : public C {  
public:  
   virtual void f() new {  
      System::Console::WriteLine("D::f() called");  
   }  
  
   virtual void g() override {  
      System::Console::WriteLine("D::g() called");  
   }  
};  
  
ref class E : public D {  
public:  
   virtual void f() override {  
      System::Console::WriteLine("E::f() called");  
   }  
};  
  
int main() {  
   D^ d = gcnew D;  
   C^ c = gcnew D;  
  
   c->f();   // calls C::f  
   d->f();   // calls D::f  
  
   c->g();   // calls D::g  
   d->g();   // calls D::g  
  
   D ^ e = gcnew E;  
   e->f();   // calls E::f  
}  
```  
  
 **Resultados**  
  
  **C::f\(\) called**  
 **D::f\(\) called**  
 **D::g\(\) called**  
 **D::g\(\) called**  
 **E::f\(\) called**   
## Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)