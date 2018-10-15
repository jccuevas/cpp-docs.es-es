---
title: Compatibilidad de compilador para Type Traits (C++ / c++ / CLI y c++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- __is_simple_value_class
- __has_trivial_destructor
- __has_assign
- __is_union
- __is_class
- __is_abstract
- __has_trivial_assign
- __has_virtual_destructor
- __is_ref_array
- __is_base_of
- __has_copy
- __is_polymorphic
- __has_nothrow_constructor
- __is_ref_class
- __is_delegate
- __is_convertible_to
- __is_value_class
- __is_interface_class
- __has_nothrow_copy
- __is_sealed
- __has_trivial_constructor
- __has_trivial_copy
- __is_enum
- __has_nothrow_assign
- __has_finalizer
- __is_empty
- __is_pod
- __has_user_destructor
dev_langs:
- C++
helpviewer_keywords:
- __is_class keyword [C++]
- __is_pod keyword [C++]
- __is_delegate keyword [C++]
- __is_value_class keyword [C++]
- __has_copy keyword [C++]
- __has_nothrow_copy keyword [C++]
- __is_interface_class keyword [C++]
- __is_sealed keyword [C++]
- __is_convertible_to keyword [C++]
- __is_ref_class keyword [C++]
- __has_trivial_copy keyword [C++]
- __has_user_destructor keyword [C++]
- __is_abstract keyword [C++]
- __is_empty keyword [C++]
- __has_trivial_assign keyword [C++]
- __has_nothrow_constructor keyword [C++]
- __is_ref_array keyword [C++]
- __is_base_of keyword [C++]
- __has_nothrow_assign keyword [C++]
- __has_virtual_destructor keyword [C++]
- __has_finalizer keyword [C++]
- __is_union keyword [C++]
- __has_assign keyword [C++]
- __has_trivial_destructor keyword [C++]
- __is_polymorphic keyword [C++]
- __is_enum keyword [C++]
- __is_simple_value_class keyword [C++]
- __has_trivial_constructor keyword [C++]
ms.assetid: cd440630-0394-48c0-a16b-1580b6ef5844
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: dfa3f599da4594e9cb0d416def1846b9937664f8
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328543"
---
# <a name="compiler-support-for-type-traits-ccli-and-ccx"></a>Compatibilidad de compilador para Type Traits (C++ / c++ / CLI y c++ / CX)

El compilador de Microsoft C++ admite *rasgos de tipos* C / c++ / CLI y c++ / extensiones CX, que indican diversas características de un tipo en tiempo de compilación.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="remarks"></a>Comentarios

Los rasgos de tipo son especialmente útiles para los programadores que escriben las bibliotecas.

En la lista siguiente contiene los rasgos de tipo que son compatibles con el compilador. Todos los rasgos de tipo devuelven **false** si no se cumple la condición especificada por el nombre del rasgo de tipo.

(En la lista siguiente, los ejemplos de código se escriben solo en C++ / c++ / CLI. Pero el rasgo de tipo correspondiente también se admite en C++ / c++ / CX, a menos que se indique lo contrario. El término "tipo de plataforma" hace referencia a tipos en tiempo de ejecución de Windows o en tipos common language runtime.)

- `__has_assign(` *Tipo* `)`

   Devuelve **true** si la plataforma o tipo nativo tiene un operador de asignación de copia.

    ```cpp
    ref struct R {
    void operator=(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_assign(R));
    }
    ```

- `__has_copy(` *Tipo* `)`

   Devuelve **true** si la plataforma o tipo nativo tiene un constructor de copias.

    ```cpp
    ref struct R {
    R(R% r) {}
    };

    int main() {
    System::Console::WriteLine(__has_copy(R));
    }
    ```

- `__has_finalizer(` *Tipo* `)`

   (No se admite en C++ / c++ / CX.) Devuelve **true** si el tipo CLR tiene un finalizador. Consulte [destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers) para obtener más información.

    ```cpp
    using namespace System;
    ref struct R {
    ~R() {}
    protected:
    !R() {}
    };

    int main() {
    Console::WriteLine(__has_finalizer(R));
    }
    ```

- `__has_nothrow_assign(` *Tipo* `)`

   Devuelve **true** si un operador de asignación de copia tiene una especificación de excepción vacía.

    ```cpp
    #include <stdio.h>
    struct S {
    void operator=(S& r) throw() {}
    };

    int main() {
    __has_nothrow_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_constructor(` *Tipo* `)`

   Devuelve **true** si el constructor predeterminado tiene una especificación de excepción vacía.

    ```cpp
    #include <stdio.h>
    struct S {
    S() throw() {}
    };

    int main() {
    __has_nothrow_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_nothrow_copy(` *Tipo* `)`

   Devuelve **true** si el constructor de copia tiene una especificación de excepción vacía.

    ```cpp
    #include <stdio.h>
    struct S {
    S(S& r) throw() {}
    };

    int main() {
    __has_nothrow_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_assign(` *Tipo* `)`

   Devuelve **true** si el tipo tiene un operador de asignación triviales, generado por el compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_assign(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_constructor(` *Tipo* `)`

   Devuelve **true** si el tipo tiene un constructor trivial, generado por el compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_constructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_copy(` *Tipo* `)`

   Devuelve **true** si el tipo tiene un constructor de copias trivial, generado por el compilador.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_copy(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_trivial_destructor(` *Tipo* `)`

   Devuelve **true** si el tipo tiene un destructor trivial, generado por el compilador.

    ``` cpp 
    // has_trivial_destructor.cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __has_trivial_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__has_user_destructor(` *Tipo* `)`

   Devuelve **true** si la plataforma o tipo nativo tiene un destructor declarado por el usuario.

    ```cpp
    // has_user_destructor.cpp

    using namespace System;
    ref class R {
    ~R() {}
    };

    int main() {
    Console::WriteLine(__has_user_destructor(R));
    }
    ```

- `__has_virtual_destructor(` *Tipo* `)`

   Devuelve **true** si el tipo tiene un destructor virtual.

   `__has_virtual_destructor` también funciona en tipos de plataforma, y cualquier destructor definido por el usuario en un tipo de plataforma es un destructor virtual.

    ```cpp
    // has_virtual_destructor.cpp
    #include <stdio.h>
    struct S {
    virtual ~S() {}
    };

    int main() {
    __has_virtual_destructor(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_abstract(` *Tipo* `)`

   Devuelve **true** si el tipo es un tipo abstracto. Para obtener más información sobre tipos abstractos nativos, vea [clases abstractas](../cpp/abstract-classes-cpp.md).

   `__is_abstract` también funciona en los tipos de plataforma. Una interfaz con al menos un miembro es un tipo abstracto, como también lo es un tipo de referencia con al menos un miembro abstracto. Para obtener más información sobre tipos abstractos de plataforma, consulte [abstracta](../windows/abstract-cpp-component-extensions.md).

    ```cpp
    // is_abstract.cpp
    #include <stdio.h>
    struct S {
    virtual void Test() = 0;
    };

    int main() {
    __is_abstract(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_base_of(` `base` `,` `derived` `)`

   Devuelve **true** si el primer tipo es una clase base del segundo tipo, of si ambos tipos son iguales.

   `__is_base_of` también funciona en tipos de plataforma. Por ejemplo, devolverá **true** si el primer tipo es un [clase interface](../windows/interface-class-cpp-component-extensions.md) y el segundo tipo implementa la interfaz.

    ```cpp
    // is_base_of.cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    __is_base_of(S, T) == true ?
    printf("true\n") : printf("false\n");

    __is_base_of(S, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_class(` *Tipo* `)`

   Devuelve **true** si el tipo es una clase o struct nativo.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_class(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_convertible_to(` `from` `,`  `to` `)`

   Devuelve **true** si el primer tipo se puede convertir al tipo de segundo.

    ```cpp
    #include <stdio.h>
    struct S {};
    struct T : public S {};

    int main() {
    S * s = new S;
    T * t = new T;
    s = t;
    __is_convertible_to(T, S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_delegate(` *Tipo* `)`

   Devuelve **true** si `type` es un delegado. Para obtener más información, consulte [delegar (C++ / c++ / CLI y c++ / CX)](../windows/delegate-cpp-component-extensions.md).

    ```cpp
    delegate void MyDel();
    int main() {
    System::Console::WriteLine(__is_delegate(MyDel));
    }
    ```

- `__is_empty(` *Tipo* `)`

   Devuelve **true** si el tipo no tiene ningún miembro de datos de instancia.

    ```cpp
    #include <stdio.h>
    struct S {
    int Test() {}
    static int i;
    };
    int main() {
    __is_empty(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_enum(` *Tipo* `)`

   Devuelve **true** si el tipo es una enumeración nativa.

    ```cpp
    // is_enum.cpp
    #include <stdio.h>
    enum E { a, b };

    struct S {
    enum E2 { c, d };
    };

    int main() {
    __is_enum(E) == true ?
    printf("true\n") : printf("false\n");

    __is_enum(S::E2) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_interface_class(` *Tipo* `)`

   Devuelve **true** si pasa una interfaz de plataforma. Para obtener más información, consulte [clase de interfaz](../windows/interface-class-cpp-component-extensions.md).

    ```cpp
    // is_interface_class.cpp

    using namespace System;
    interface class I {};
    int main() {
    Console::WriteLine(__is_interface_class(I));
    }
    ```

- `__is_pod(` *Tipo* `)`

   Devuelve **true** si el tipo es una clase o unión con ningún constructor o miembro no estático privado o protegido, ninguna clase base y ninguna función virtual. Vea el estándar de C++, secciones 8.5.1/1, 9/4 y 10 3.9 para más información sobre POD.

   `__is_pod` devuelve false en tipos fundamentales.

    ```cpp
    #include <stdio.h>
    struct S {};

    int main() {
    __is_pod(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_polymorphic(` *Tipo* `)`

   Devuelve **true** si un tipo nativo tiene funciones virtuales.

    ```cpp
    #include <stdio.h>
    struct S {
    virtual void Test(){}
    };

    int main() {
    __is_polymorphic(S) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_ref_array(` *Tipo* `)`

   Devuelve **true** si pasa una matriz de plataforma. Para obtener más información, consulte [matrices](../windows/arrays-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    int main() {
    array<int>^ x = gcnew array<int>(10);
    Console::WriteLine(__is_ref_array(array<int>));
    }
    ```

- `__is_ref_class(` *Tipo* `)`

   Devuelve **true** si pasa una clase de referencia. Para obtener más información sobre los tipos de referencia definidos por el usuario, consulte [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    int main() {
    Console::WriteLine(__is_ref_class(Buffer));
    Console::WriteLine(__is_ref_class(R));
    }
    ```

- `__is_sealed(` *Tipo* `)`

   Devuelve **true** si pasa una plataforma o tipo nativo marcado como sealed. Para obtener más información, consulte [sealed](../windows/sealed-cpp-component-extensions.md).

    ```cpp
    ref class R sealed{};
    int main() {
    System::Console::WriteLine(__is_sealed(R));
    }
    ```

- `__is_simple_value_class(` *Tipo* `)`

   Devuelve **true** si pasa un tipo de valor que no contiene referencias al montón de recolección. Para obtener más información sobre los tipos de valor definido por el usuario, consulte [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    using namespace System;
    ref class R {};
    value struct V {};
    value struct V2 {
    R ^ r;   // not a simnple value type
    };

    int main() {
    Console::WriteLine(__is_simple_value_class(V));
    Console::WriteLine(__is_simple_value_class(V2));
    }
    ```

- `__is_union(` *Tipo* `)`

   Devuelve **true** si un tipo es una unión.

    ```cpp
    #include <stdio.h>
    union A {
    int i;
    float f;
    };

    int main() {
    __is_union(A) == true ?
    printf("true\n") : printf("false\n");
    }
    ```

- `__is_value_class(` *Tipo* `)`

   Devuelve **true** si pasa un tipo de valor. Para obtener más información sobre los tipos de valor definido por el usuario, consulte [clases y Structs](../windows/classes-and-structs-cpp-component-extensions.md).

    ```cpp
    value struct V {};

    int main() {
    System::Console::WriteLine(__is_value_class(V));
    }
    ```

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

El `__has_finalizer(` *tipo* `)` rasgo de tipo no se admite porque esta plataforma no admite los finalizadores.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

(No hay ninguna observación específica de la plataforma para esta característica).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

**Ejemplo**

En el ejemplo de código siguiente se muestra cómo usar una plantilla de clase para exponer un rasgo de tipo de compilador para una compilación de `/clr`. Para obtener más información, consulte [en tiempo de ejecución de Windows y plantillas administradas](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).

```cpp
// compiler_type_traits.cpp
// compile with: /clr
using namespace System;

template <class T>
ref struct is_class {
   literal bool value = __is_ref_class(T);
};

ref class R {};

int main () {
   if (is_class<R>::value)  
      Console::WriteLine("R is a ref class");
   else
      Console::WriteLine("R is not a ref class");
}
```

```Output
R is a ref class
```

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)