---
title: sealed (C++ / c++ / CLI y c++ / CX) | Microsoft Docs
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
dev_langs:
- C++
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ee0ea65267320a4730c543cec978c2675ef1cc57
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50071958"
---
# <a name="sealed--ccli-and-ccx"></a>sealed (C++ / c++ / CLI y c++ / CX)

**sellado** es una palabra de clave contextual para las clases ref que indica que no se puede invalidar un miembro virtual o un tipo no se puede usar como tipo base.

> [!NOTE]
> El ISO C ++ 11 estándar lenguaje introdujo el [final](../cpp/final-specifier.md) palabra clave. Use **final** en clases estándar y **sealed** en las clases ref.

## <a name="all-runtimes"></a>Todos los runtimes

## <a name="syntax"></a>Sintaxis

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parámetros

*identifier*<br/>
Nombre de la función o clase.

*tipo de valor devuelto*<br/>
Tipo devuelto por una función.

## <a name="remarks"></a>Comentarios

En el primer ejemplo de sintaxis, una clase está sellada. En el segundo ejemplo, una función virtual está sellada.

Use la **sealed** palabra clave para las clases ref y sus funciones de miembro virtual. Para obtener más información, consulte [especificadores de invalidación y compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Puede detectar en tiempo de compilación si un tipo está sellado usando el `__is_sealed(type)` rasgo de tipo. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

**sellado** es una palabra clave contextual.  Para obtener más información, consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Consulte [clases y structs Ref](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

Este ejemplo de código siguiente muestra el efecto de **sealed** en un miembro virtual.

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

```Output
X::f override of I1::f
X::f override of I1::g
Y::f override of I1::f
```

En el ejemplo de código siguiente se muestra cómo marcar una clase como sellada.

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

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)