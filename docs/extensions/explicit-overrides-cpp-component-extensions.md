---
title: Invalidaciones explícitas (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- overriding, override [C++]
ms.assetid: 4ec3eaf5-163b-4df8-8f16-7a2ec04c3d0f
ms.openlocfilehash: c199301794daaa140ede2fd99b0ae755cea70f97
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172378"
---
# <a name="explicit-overrides--ccli-and-ccx"></a>Invalidaciones explícitas (C++/CLI y C++/CX)

En este tema se explica cómo invalidar explícitamente un miembro de una clase base o interfaz. Solo debe usarse una invalidación con nombre (explícita) para invalidar un método con un método derivado con otro nombre.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="syntax"></a>Sintaxis

```cpp
overriding-function-declarator = type::function [,type::function] { overriding-function-definition }
overriding-function-declarator = function { overriding-function-definition }
```

### <a name="parameters"></a>Parámetros

*overriding-function-declarator*<br/>
Lista de argumentos, nombres y tipos de valor devuelto de la función de invalidación.  Tenga en cuenta que la función de invalidación no debe tener el mismo nombre que la función que se invalida.

*type*<br/>
Tipo base que contiene una función que se va a invalidar.

*function*<br/>
Lista delimitada por comas de uno o varios nombres de función que se van a invalidar.

*overriding-function-definition*<br/>
Instrucciones de cuerpo de función que definen la función de invalidación.

### <a name="remarks"></a>Observaciones

Use invalidaciones explícitas para crear un alias para una firma de método o para proporcionar implementaciones diferentes para los métodos con la misma firma.

Para obtener información sobre cómo modificar el comportamiento de los tipos y los miembros de tipo heredados, consulte [Override Specifiers](override-specifiers-cpp-component-extensions.md) (Especificadores de invalidación).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Observaciones

Para obtener información sobre las invalidaciones explícitas en código nativo o compilado con `/clr:oldSyntax`, consulte el artículo sobre [las invalidaciones explícitas](../cpp/explicit-overrides-cpp.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se muestran una invalidación sencilla e implícita y la implementación de un miembro en una interfaz base, sin invalidaciones explícitas.

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

En el ejemplo de código siguiente se muestra cómo implementar todos los miembros de interfaz con una firma común, con la sintaxis de invalidación explícita.

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

En el ejemplo de código siguiente se muestra cómo puede una invalidación de función tener un nombre distinto del de la función que implementa.

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

En el ejemplo de código siguiente se muestra una implementación de interfaz explícita que implementa una colección con seguridad de tipos.

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

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
