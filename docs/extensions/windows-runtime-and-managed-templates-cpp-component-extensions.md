---
title: Windows Runtime y plantillas administradas (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: 5765370e611e5822b3b2d156d2eee5d21e5b453d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376305"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime y plantillas administradas (C++/CLI y C++/CX)

Las plantillas le permiten definir un prototipo de un tipo de Windows Runtime o Common Language Runtime y, a continuación, crear una instancia de las variaciones de ese tipo mediante diversos parámetros de tipo de plantilla.

## <a name="all-runtimes"></a>Todos los runtimes

Puede crear plantillas a partir de tipos de referencia o valor.  Para obtener más información sobre la creación de tipos de referencia o valor, consulte [Classes and Structs](classes-and-structs-cpp-component-extensions.md) (Clases y structs).

Para obtener más información sobre las plantillas de clase de C++ estándar, consulte [Plantillas de clase](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Existen algunas limitaciones a la hora de crear plantillas de clase a partir de tipos administrados, que se muestran en los ejemplos de código siguientes.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

Es posible crear una instancia de un tipo genérico con un parámetro de plantilla de tipo administrado, pero no puede crear una instancia de una plantilla administrada con un parámetro de plantilla de tipo genérico. Esto se debe a que los tipos genéricos se resuelven en tiempo de ejecución. Para obtener más información, consulte [Generics and Templates (C++/CLI)](generics-and-templates-visual-cpp.md) [(Genéricos y plantillas (C++/CLI)].

```cpp
// managed_templates.cpp
// compile with: /clr /c

generic<class T>
ref class R;

template<class T>
ref class Z {
   // Instantiate a generic with a template parameter.
   R<T>^ r;    // OK
};

generic<class T>
ref class R {
   // Cannot instantiate a template with a generic parameter.
   Z<T>^ z;   // C3231
};
```

Un tipo genérico o función no se puede anidar en una plantilla administrada.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

No puede obtener acceso a las plantillas definidas en un ensamblado al que se hace referencia con la sintaxis del lenguaje C++/CLI, pero puede usar la reflexión. Si no se crea una instancia de una plantilla, no se emite en los metadatos. Si se crea una instancia de una plantilla, solo aparecerán en los metadatos las funciones miembro a las que se hace referencia.

```cpp
// managed_templates_3.cpp
// compile with: /clr

// Will not appear in metadata.
template<class T> public ref class A {};

// Will appear in metadata as a specialized type.
template<class T> public ref class R {
public:
   // Test is referenced, will appear in metadata
   void Test() {}

   // Test2 is not referenced, will not appear in metadata
   void Test2() {}
};

// Will appear in metadata.
generic<class T> public ref class G { };

public ref class S { };

int main() {
   R<int>^ r = gcnew R<int>;
   r->Test();
}
```

Puede cambiar el modificador administrado de una clase en una especialización parcial o explícita de una plantilla de clase.

```cpp
// managed_templates_4.cpp
// compile with: /clr /c

// class template
// ref class
template <class T>
ref class A {};

// partial template specialization
// value type
template <class T>
value class A <T *> {};

// partial template specialization
// interface
template <class T>
interface class A<T%> {};

// explicit template specialization
// native class
template <>
class A <int> {};
```

## <a name="see-also"></a>Consulte también

[Extensiones de componentes para .NET y UWP](component-extensions-for-runtime-platforms.md)
