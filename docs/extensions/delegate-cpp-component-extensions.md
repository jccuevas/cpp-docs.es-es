---
title: delegate  (C++/CLI and C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
ms.openlocfilehash: 388ccb28c9311b4727199e6b7324771c24c2906d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172443"
---
# <a name="delegate--ccli-and-ccx"></a>delegate  (C++/CLI and C++/CX)

Declara un tipo que representa un puntero de función.

## <a name="all-runtimes"></a>Todos los runtimes

Windows Runtime y Common Language Runtime admiten delegados.

### <a name="remarks"></a>Observaciones

**delegate** es una palabra clave contextual. Para obtener más información, consulte [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) (Palabras clave contextuales).

Para detectar en tiempo de compilación si un tipo es un delegado, use el rasgo de tipo `__is_delegate()`. Para más información, consulte [Compatibilidad del compilador con rasgos de tipo](compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

C++/CX admite delegados con la sintaxis siguiente.

### <a name="syntax"></a>Sintaxis

```cpp
access
delegate
return-type
delegate-type-identifier
(
[ parameters ]
)
```

### <a name="parameters"></a>Parámetros

*acceso*<br/>
(opcional) La accesibilidad del delegado, que puede ser **public** (valor predeterminado) o **private**. El prototipo de función también se puede calificar con las palabras clave **const** o **volatile**.

*return-type*<br/>
El tipo de valor devuelto del prototipo de función.

*delegate-type-identifier*<br/>
El nombre del tipo de delegado declarado.

*parameters*<br/>
(Opcional) Los tipos e identificadores del prototipo de función.

### <a name="remarks"></a>Observaciones

Use *delegate-type-identifier* para declarar un evento con el mismo prototipo que el delegado. Para información, consulte [Delegados (C++/CX)](../cppcx/delegates-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Common language runtime admite delegados con la sintaxis siguiente.

### <a name="syntax"></a>Sintaxis

```cpp
access
delegate
function_declaration
```

### <a name="parameters"></a>Parámetros

*acceso*<br/>
(opcional) La accesibilidad del delegado fuera del ensamblado puede ser pública o privada.  El valor predeterminado es privada.  Dentro de una clase, un delegado puede tener cualquier accesibilidad.

*function_declaration*<br/>
La signatura de la función que se puede enlazar al delegado. El tipo de valor devuelto de un delegado puede ser cualquier tipo administrado. Por motivos de interoperabilidad, se recomienda que el tipo de valor devuelto de un delegado sea un tipo CLS.

Para definir un delegado sin enlazar, el primer parámetro de *function_declaration* deben tener el tipo del puntero **this** del objeto.

### <a name="remarks"></a>Observaciones

Los delegados son multidifusión: el "puntero de función" se puede enlazar a uno o más métodos dentro de una clase administrada. La palabra clave **delegate** define un tipo de delegado de multidifusión con una signatura de método específica.

Un delegado también se puede enlazar a un método de una clase de valor, como un método estático.

Un delegado tiene las siguientes características:

- Hereda de `System::MulticastDelegate`.

- Tiene un constructor que toma dos argumentos: un puntero a una clase administrada o NULL (en el caso del enlace a un método estático) y un método completo del tipo especificado.

- Tiene un método denominado `Invoke`, cuya signatura coincide con la signatura declarada del delegado.

Cuando se invoca un delegado, sus funciones se llaman en el orden en que se asociaron.

El valor devuelto de un delegado es el valor devuelto por su última función miembro asociada.

Los delegados no se pueden sobrecargar.

Los delegados se pueden enlazar o desenlazar.

Cuando se crea una instancia de un delegado enlazado, el primer argumento será una referencia a un objeto. El segundo argumento de una instancia de delegado será la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor. El segundo argumento de una instancia de delegado debe nombrar el método con la sintaxis de ámbito de clase completa y aplicar la dirección del operador.

Cuando se crea una instancia de un delegado sin enlazar, el primer argumento será la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor. El argumento debe nombrar el método con la sintaxis de ámbito de clase completa y aplicar la dirección del operador.

Cuando se crea un delegado a una función global o estática, solo se requiere un parámetro: la función (opcionalmente, la dirección de la función).

Para más información sobre delegados, consulte

- [Cómo: Definir y usar delegados (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Delegados genéricos (C++/CLI)](generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se muestra cómo declarar, inicializar e invocar delegados.

```cpp
// mcppv2_delegate.cpp
// compile with: /clr
using namespace System;

// declare a delegate
public delegate void MyDel(int i);

ref class A {
public:
   void func1(int i) {
      Console::WriteLine("in func1 {0}", i);
   }

   void func2(int i) {
      Console::WriteLine("in func2 {0}", i);
   }

   static void func3(int i) {
      Console::WriteLine("in static func3 {0}", i);
   }
};

int main () {
   A ^ a = gcnew A;

   // declare a delegate instance
   MyDel^ DelInst;

   // test if delegate is initialized
   if (DelInst)
      DelInst(7);

   // assigning to delegate
   DelInst = gcnew MyDel(a, &A::func1);

   // invoke delegate
   if (DelInst)
      DelInst(8);

   // add a function
   DelInst += gcnew MyDel(a, &A::func2);

   DelInst(9);

   // remove a function
   DelInst -= gcnew MyDel(a, &A::func1);

   // invoke delegate with Invoke
   DelInst->Invoke(10);

   // make delegate to static function
   MyDel ^ StaticDelInst = gcnew MyDel(&A::func3);
   StaticDelInst(11);
}
```

```Output
in func1 8

in func1 9

in func2 9

in func2 10

in static func3 11
```

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
