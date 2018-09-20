---
title: New (nueva ranura en vtable) (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 1a9a5704-f02f-46ae-ad65-f0f2b6dbabc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: b5dc0f490da43b4a2a2befa22f2902e7bfce51ca
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46420925"
---
# <a name="new-new-slot-in-vtable--c-component-extensions"></a>new (nueva ranura en vtable) (Extensiones de componentes de C++)

El **nuevo** palabra clave indica que un miembro virtual obtendrá una nueva ranura en vtable.

## <a name="all-runtimes"></a>Todos los runtimes

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

No se admite en Windows en tiempo de ejecución.

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

En un `/clr` compilación, **nuevo** indica que un miembro virtual obtendrá una nueva ranura en vtable; que la función no invalida un método de clase base.

**nueva** hace que el modificador newslot se agregue al IL para la función.  Para obtener más información sobre newslot, vea:

- [Método MethodInfo.GetBaseDefinition](https://msdn.microsoft.com/library/system.reflection.methodinfo.getbasedefinition.aspx)

- [Enumeración MethodAttributes](https://msdn.microsoft.com/library/system.reflection.methodattributes.aspx)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

El ejemplo siguiente muestra el efecto de **nuevo**.

```cpp
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

```Output
C::f() called

D::f() called

D::g() called

D::g() called

E::f() called
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)<br/>
[Especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md)