---
title: New (nueva ranura en vtable) (extensiones de componentes de C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f208a62fd49e7aea67acf5b7e3e49d3571f8d910
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nueva ranura en vtable) (Extensiones de componentes de C++)
La palabra clave `new` indica que un miembro virtual obtendrá una nueva ranura en vtable.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 (No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 No se admite en tiempo de ejecución de Windows.  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 En un **/CLR** compilación, `new` indica que un miembro virtual obtendrá una nueva ranura en vtable; que la función no reemplaza un método de clase base.  
  
 `new` hace que el modificador newslot se agregue al IL para la función.  Para obtener más información sobre newslot, vea:  
  
-   [Método MethodInfo.GetBaseDefinition](https://msdn.microsoft.com/en-us/library/system.reflection.methodinfo.getbasedefinition.aspx)  
  
-   [Enumeración MethodAttributes](https://msdn.microsoft.com/en-us/library/system.reflection.methodattributes.aspx)  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
### <a name="examples"></a>Ejemplos  
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
  
 **Salida**  
  
```Output  
C::f() called  
  
D::f() called  
  
D::g() called  
  
D::g() called  
  
E::f() called  
```  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)   
 [Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)