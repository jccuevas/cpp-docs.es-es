---
title: sealed  (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- sealed_cpp
- sealed
helpviewer_keywords:
- sealed keyword [C++]
ms.assetid: 3d0d688a-41aa-45f5-a25a-65c44206521e
ms.openlocfilehash: 493f6597d146480714848b37154cc8bacd37113a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516010"
---
# <a name="sealed--ccli-and-ccx"></a>sealed  (C++/CLI y C++/CX)

**sealed** es una palabra clave contextual para las clases de referencia que indica que no se puede reemplazar un miembro virtual o que no se puede usar un tipo como tipo base.

> [!NOTE]
> El lenguaje de la norma ISO C++11 presentó la palabra clave [final](../cpp/final-specifier.md). Use **final** en las clases estándar y **sealed** en las clases de referencia.

## <a name="all-runtimes"></a>Todos los runtimes

## <a name="syntax"></a>Sintaxis

```cpp
ref class identifier sealed {...};
virtual return-type identifier() sealed {...};
```

### <a name="parameters"></a>Parámetros

*identifier*<br/>
Nombre de la función o clase.

*return-type*<br/>
Tipo devuelto por una función.

## <a name="remarks"></a>Comentarios

En el primer ejemplo de sintaxis, una clase está sellada. En el segundo ejemplo, una función virtual está sellada.

Use la palabra clave **sealed** para las clases de referencia y sus funciones miembro virtuales. Para obtener más información, consulte el artículo sobre [los especificadores de invalidación y las compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

Puede detectar en tiempo de compilación si un tipo está sellado usando el rasgo de tipo `__is_sealed(type)`. Para obtener más información, consulte [Compiler Support for Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md) (Compatibilidad de compilador con rasgos de tipo).

**sealed** es una palabra clave contextual.  Para obtener más información, consulte [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) (Palabras clave contextuales).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Consulte el artículo sobre [las clases de referencia y structs](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

(No hay notas para esta característica de lenguaje que solo se apliquen a Common Language Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En este ejemplo de código que se muestra a continuación, puede ver el efecto de **sealed** en un miembro virtual.

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

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)