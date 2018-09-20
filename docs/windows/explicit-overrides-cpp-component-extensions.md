---
title: Invalidaciones explícitas (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ba6ed66359ee833b51154e47f8f6c26c0de8994c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408952"
---
# <a name="explicit-overrides--c-component-extensions"></a>Invalidaciones explícitas (extensiones componentes de C++)

En este tema se describe cómo reemplazar explícitamente un miembro de una clase base o interfaz. Solo debe usarse una invalidación con nombre (explícita) para invalidar un método con un método derivado tiene un nombre diferente.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="syntax"></a>Sintaxis

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parámetros

*declarador de función reemplazar*<br/>
La lista Tipo, el nombre y el argumento devuelta de la función de reemplazo.  Tenga en cuenta que la función de reemplazo no deben tener el mismo nombre que la función que se va a reemplazar.

*type*<br/>
El tipo base que contiene una función para invalidar.

*function*<br/>
Una lista delimitada por comas de uno o más nombres de función para invalidar.

*definición de función reemplazar*<br/>
Las instrucciones del cuerpo de función que definen la función de reemplazo.

### <a name="remarks"></a>Comentarios

Use explícita invalidaciones para crear un alias para una firma de método o para proporcionar diferentes implementaciones de métodos witht la misma firma.

Para obtener información acerca de cómo modificar el comportamiento de los tipos heredados y miembros de tipos heredados, vea [especificadores de invalidación](../windows/override-specifiers-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

Para información explícita acerca de las invalidaciones en código nativo o código compilado con `/clr:oldSyntax`, consulte [invalidaciones explícitas](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestra un reemplazo simple e implícita y la implementación de un miembro en una interfaz base, no mediante invalidaciones explícitas.

```cpp
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

```Output
X::f override of I1::f
```

El ejemplo de código siguiente muestra cómo implementar a todos los miembros de interfaz con una firma común, con la sintaxis de invalidación explícita.

```cpp
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

```Output
X::f override of I1::f and I2::f
X::f override of I1::f and I2::f
```

El ejemplo de código siguiente muestra cómo un reemplazo de la función puede tener un nombre diferente de la función que se implementa.

```cpp
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

```Output
X::g
```

En el ejemplo de código siguiente se muestra una implementación de interfaz explícita que implementa una colección de tipo seguro.

```cpp
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

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)