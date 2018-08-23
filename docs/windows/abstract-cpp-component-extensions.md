---
title: abstract (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- abstract
- abstract_cpp
dev_langs:
- C++
helpviewer_keywords:
- abstract keyword [C++]
ms.assetid: cbae3408-0378-4ac8-b70d-c016b381a6d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 463848ea5f01bf232850d548c9f4255c07409254
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42611004"
---
# <a name="abstract--c-component-extensions"></a>abstract (Extensiones de componentes de C++)

El **abstracta** palabra clave declara si:

- Un tipo se puede utilizar como un tipo base, pero no puede instanciarse por sí mismo.

- Un tipo de función de miembro solo puede definirse en un tipo derivado.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="syntax"></a>Sintaxis

```cpp
      class-declaration
      class-identifier
      abstract {}
virtualreturn-typemember-function-identifier() abstract ;
```

### <a name="remarks"></a>Comentarios

La primera sintaxis de ejemplo declara una clase como abstracta. El *declaración de clase* componente puede ser una declaración de C++ nativa (**clase** o **struct**), o una declaración de la extensión de C++ (**clase ref** o **ref struct**) si el `/ZW` o `/clr` se especificó la opción del compilador.

La segunda sintaxis de ejemplo declara una función de miembro virtual como abstracta. Declarar una función como abstracta es lo mismo que declararla como función virtual pura. Declarar una función de miembro abstracta también provoca que la clase de inclusión sea declarada abstracta.

El **abstracta** se admite la palabra clave en el código específico de plataforma y nativo; es decir, se puede compilar con o sin el `/ZW` o `/clr` opción del compilador.

Puede detectar en tiempo de compilación si un tipo es abstracto con el `__is_abstract(type)` rasgo de tipo. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

El **abstracta** palabra clave es un especificador de reemplazo contextual. Para obtener más información acerca de las palabras clave contextuales, vea [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md). Para obtener más información sobre los especificadores de invalidación, vea [Cómo: declarar especificadores de reemplazo en compilaciones nativas](../dotnet/how-to-declare-override-specifiers-in-native-compilations-cpp-cli.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Para obtener más información, consulte [clases y structs Ref](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo de código siguiente se genera un error porque clase `X` está marcado como **abstracta**.

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

En el ejemplo de código siguiente se genera un error porque crea una instancia de una clase nativa que está marcado como **abstracta**. Este error ocurrirá con o sin la opción del compilador `/clr`.

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

En el ejemplo de código siguiente se genera un error porque función `f` incluye una definición, pero está marcado como **abstracta**. La instrucción final del ejemplo muestra que declarar una función virtual como abstracta equivale a declarar una función virtual como pura.

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

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)