---
title: Windows Runtime y plantillas administradas (C++ / c++ / CLI y c++ / CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- templates, with CLR types
ms.assetid: cf59d16b-5514-448b-9a95-e0b4fcb616a6
ms.openlocfilehash: cbd66f3ddf41602f7ed9a73f3a334bb86f1f3705
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471479"
---
# <a name="windows-runtime-and-managed-templates-ccli-and-ccx"></a>Windows Runtime y plantillas administradas (C++ / c++ / CLI y c++ / CX)

Las plantillas le permiten definir un prototipo de un tiempo de ejecución de Windows o un tipo common language runtime y, a continuación, crear instancias de las variaciones de ese tipo mediante el uso de parámetros de tipo de plantilla diferente.

## <a name="all-runtimes"></a>Todos los runtimes

Puede crear plantillas de tipos de valor o referencia.  Para obtener más información acerca de cómo crear tipos de valor o referencia, consulte [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

Para obtener más información acerca de las plantillas de clase estándares de C++, vea [plantillas de clase](../cpp/class-templates.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Existen algunas limitaciones a la creación de plantillas de clase de tipos administrados, que se muestran en los ejemplos de código siguiente.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

Es posible crear instancias de un tipo genérico con un parámetro de plantilla de tipo administrado, pero no se puede crear una instancia de una plantilla administrada con un parámetro de tipo genérico. Esto es porque los tipos genéricos se resuelven en tiempo de ejecución. Para obtener más información, consulte [genéricos y plantillas (C++ / c++ / CLI)](../windows/generics-and-templates-visual-cpp.md).

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

Un tipo genérico o una función no se puede anidar en una plantilla administrada.

```cpp
// managed_templates_2.cpp
// compile with: /clr /c

template<class T> public ref class R {
   generic<class T> ref class W {};   // C2959
};
```

No se puede obtener acceso a las plantillas definidas en un ensamblado de referencia con C++ / c++ / sintaxis del lenguaje de CLI, pero se puede usar la reflexión. Si no se crea una instancia de una plantilla, no se emite en los metadatos. Si se crea una instancia de una plantilla, solo las funciones de miembro que se hace referencia aparecen en los metadatos.

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

Puede cambiar el modificador administrado de una clase en una especialización parcial o una especialización explícita de una plantilla de clase.

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

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)