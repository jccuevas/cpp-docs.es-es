---
title: Delegate (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- delegate_cpp
- delegate
dev_langs:
- C++
helpviewer_keywords:
- delegate keyword [C++]
ms.assetid: 03caf23d-7873-4a23-9b34-becf42aaf429
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 46b09b5cbe74849c3dc08e8faee3ee4ca645a55b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602939"
---
# <a name="delegate--c-component-extensions"></a>delegate (Extensiones de componentes de C++)

Declara un tipo que representa un puntero de función.

## <a name="all-runtimes"></a>Todos los runtimes

El tiempo de ejecución de Windows y el common language runtime admiten a delegados.

### <a name="remarks"></a>Comentarios

**delegar** es una palabra clave contextual. Para obtener más información, consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md).

Para detectar en tiempo de compilación si un tipo es un delegado, use el `__is_delegate()` rasgo de tipo. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

C++ / c++ / CX admite delegados con la sintaxis siguiente.

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

*access*  
(opcional) La accesibilidad del delegado, que puede ser **pública** (valor predeterminado) o **privada**. El prototipo de función también se puede calificar con el **const** o **volátil** palabras clave.

*tipo de valor devuelto*  
El tipo de valor devuelto del prototipo de función.

*identificador del tipo de delegado*  
El nombre del tipo de delegado declarado.

*Parámetros*  
(Opcional) Los tipos y los identificadores del prototipo de función.

### <a name="remarks"></a>Comentarios

Use la *delegate-type-identifier* para declarar un evento con el mismo prototipo que el delegado. Para obtener más información, consulte [delegados (C++ / c++ / CX)](../cppcx/delegates-c-cx.md).

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

*access*  
(opcional) La accesibilidad del delegado fuera del ensamblado puede ser público o privado.  El valor predeterminado es privado.  Dentro de una clase, un delegado puede tener cualquier tipo de accesibilidad.

*function_declaration*  
La firma de la función que se puede enlazar al delegado. El tipo de valor devuelto de un delegado puede ser cualquier tipo administrado. Por motivos de interoperabilidad, se recomienda que el tipo de valor devuelto de un delegado de ser un tipo CLS.

Para definir un delegado sin enlazar, el primer parámetro de *function_declaration* deben ser de tipo de la **esto** puntero para el objeto.

### <a name="remarks"></a>Comentarios

Los delegados son de multidifusión: el "puntero de función" se puede enlazar a uno o más métodos dentro de una clase administrada. El **delegar** palabra clave define un tipo de delegado de multidifusión con una firma de método concreto.

También se puede enlazar un delegado a un método de una clase de valor, como un método estático.

Un delegado tiene las siguientes características:

- Hereda de `System::MulticastDelegate`.

- Tiene un constructor que toma dos argumentos: un puntero a una clase administrada o NULL (en el caso de enlace a un método estático) y un método completo del tipo especificado.

- Tiene un método denominado `Invoke`, cuya signatura coincide con la signatura declarada del delegado.

Cuando se invoca un delegado, sus funciones se llaman en el orden en que se hayan vinculado.

El valor devuelto de un delegado es el valor devuelto desde su última función miembro asociado.

Los delegados no pueden sobrecargarse.

Pueden que los delegados se enlaza o desenlaza.

Cuando crea una instancia de un delegado enlazado, el primer argumento debe ser una referencia de objeto. El segundo argumento de la instancia de delegado cualquiera deberá ser la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor. El segundo argumento de la instancia de delegado debe nombre del método con la sintaxis de ámbito de clase completo y aplicar el operador address-of.

Cuando crea una instancia de un delegado sin enlazar, el primer argumento debe ser la dirección de un método de un objeto de clase administrada o un puntero a un método de un tipo de valor. El argumento debe nombre del método con la sintaxis de ámbito de clase completo y aplicar el operador address-of.

Al crear un delegado a una función global o estática, se requiere un solo parámetro: la función (si lo desea, la dirección de la función).

Para obtener más información sobre los delegados, vea

- [Cómo: Definir y usar delegados (C++/CLI)](../dotnet/how-to-define-and-use-delegates-cpp-cli.md)

- [Delegados genéricos (Visual C++)](../windows/generic-delegates-visual-cpp.md)

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

El ejemplo siguiente muestra cómo declarar, inicializar y los delegados se invocan.

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

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)