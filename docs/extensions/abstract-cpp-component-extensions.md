---
title: abstract (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
ms.openlocfilehash: d5060f1a0950b9b2ac2638b99ff157983944a3bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516170"
---
# <a name="abstract--ccli-and-ccx"></a>abstract (C++/CLI y C++/CX)

La palabra clave **abstract** declara si:

- Un tipo se puede utilizar como un tipo base, pero no puede instanciarse por sí mismo.

- Un tipo de función de miembro solo puede definirse en un tipo derivado.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="syntax"></a>Sintaxis

*class-declaration* *class-identifier* **abstract {}**

**virtual** *return-type* *member-function-identifier* **() abstract ;**

### <a name="remarks"></a>Comentarios

La primera sintaxis de ejemplo declara una clase como abstracta. El componente *class-declaration* puede ser una declaración nativa de C++ (**class** o **struct**), o una declaración de extensión de C++ (**ref class** o **ref struct**) si se especifica la opción del compilador `/ZW` o `/clr`.

La segunda sintaxis de ejemplo declara una función de miembro virtual como abstracta. Declarar una función como abstracta es lo mismo que declararla como función virtual pura. Declarar una función de miembro abstracta también provoca que la clase de inclusión sea declarada abstracta.

La palabra clave **abstract** se admite en el código específico de plataforma y nativo; es decir, se puede compilar con o sin la opción del compilador `/ZW` o `/clr`.

Puede detectar en tiempo de compilación si un tipo es abstracto con el rasgo de tipo `__is_abstract(type)`. Para obtener más información, consulte [Compiler Support for Type Traits](compiler-support-for-type-traits-cpp-component-extensions.md) (Compatibilidad de compilador con rasgos de tipo).

La palabra clave **abstract** es un especificador de invalidación contextual. Para obtener más información sobre las palabras clave contextuales, consulte [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) (Palabras clave contextuales). Para obtener más información sobre los especificadores de invalidación, consulte el artículo sobre [cómo declarar los especificadores de invalidación en compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para obtener más información, consulte el artículo sobre [las clases de referencia y structs](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

El ejemplo de código siguiente genera un error porque la clase `X` está marcada como **abstract**.

```cpp
// abstract_keyword.cpp
// compile with: /clr
ref class X abstract {
public:
   virtual void f() {}
};

int main() {
   X ^ MyX = gcnew X;   // C3622
}
```

El ejemplo de código siguiente genera un error porque crea una instancia de una clase nativa que está marcada como **abstract**. Este error ocurrirá con o sin la opción del compilador `/clr`.

```cpp
// abstract_keyword_2.cpp
class X abstract {
public:
   virtual void f() {}
};

int main() {
   X * MyX = new X; // C3622: 'X': a class declared as 'abstract'
                    // cannot be instantiated. See declaration of 'X'}
```

El ejemplo de código siguiente genera un error porque la función `f` incluye una definición, pero está marcada como **abstract**. La instrucción final del ejemplo muestra que declarar una función virtual como abstracta equivale a declarar una función virtual como pura.

```cpp
// abstract_keyword_3.cpp
// compile with: /clr
ref class X {
public:
   virtual void f() abstract {}   // C3634
   virtual void g() = 0 {}   // C3634
};
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
