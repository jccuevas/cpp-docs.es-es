---
title: ref class y ref struct (C++/CLI y C++/CX)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- ref class
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
ms.openlocfilehash: 9c993b134d6d359d0bc756f5e79d2f9cc137c9cf
ms.sourcegitcommit: bc1b14f29a02685f97c7ef5c098d16db6eaf369f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2019
ms.locfileid: "65788784"
---
# <a name="ref-class-and-ref-struct--ccli-and-ccx"></a>ref class y ref struct  (C++/CLI y C++/CX)

Las extensiones **ref class** o **ref struct** declaran una clase o struct cuya *duración de objetos* se administra automáticamente. Cuando el objeto ya no es accesible o queda fuera del ámbito, se libera memoria.

## <a name="all-runtimes"></a>Todos los runtimes

### <a name="syntax"></a>Sintaxis

```cpp
      class_access
      ref class
      name
      modifier :  inherit_accessbase_type {};
class_accessref structnamemodifier :  inherit_accessbase_type {};
class_accessvalue classnamemodifier :  inherit_accessbase_type {};
class_accessvalue structnamemodifier :  inherit_accessbase_type {};
```

### <a name="parameters"></a>Parámetros

*class_access*<br/>
(Opcional) La accesibilidad de la clase o el struct fuera del ensamblado. Los valores posibles son **public** y **private** (**private** es el predeterminado). Las clases o los structs anidados no pueden tener un especificador *class_access*.

*name*<br/>
Nombre de la clase o struct.

*modifier*<br/>
(Opcional) [abstract](abstract-cpp-component-extensions.md) y [sealed](sealed-cpp-component-extensions.md) son modificadores válidos.

*inherit_access*<br/>
(Opcional) La accesibilidad de *base_type*. La única accesibilidad permitida es **public** (**public** es la predeterminada).

*base_type*<br/>
(Opcional) Un tipo base. Sin embargo, un tipo de valor no puede actuar como tipo base.

Para más información, consulte las descripciones específicas del lenguaje de este parámetro en las secciones Windows Runtime y Common Language Runtime.

### <a name="remarks"></a>Comentarios

La accesibilidad del miembro predeterminado de un objeto declarado con **ref class** o **value class** es **private**. Y la accesibilidad del miembro predeterminado de un objeto declarado con **ref struct** o **value struct** es **public**.

Cuando un tipo de referencia hereda de otro tipo de referencia, las funciones virtuales de la clase base deben reemplazarse explícitamente (con [override](override-cpp-component-extensions.md)) u ocultarse (con [new [nueva ranura en vtable]](new-new-slot-in-vtable-cpp-component-extensions.md)). Las funciones de la clase derivada también deben marcarse explícitamente como **virtual**.

Para detectar en tiempo de compilación si un tipo es **ref class** o **ref struct**, o **value class** o **value struct**, use `__is_ref_class (type)`, `__is_value_class (type)` o `__is_simple_value_class (type)`. Para más información, consulte [Compatibilidad del compilador con rasgos de tipo](compiler-support-for-type-traits-cpp-component-extensions.md).

Para obtener más información sobre clases y structs, vea

- [Creación de instancias de clases y structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Semántica de pila de C++ para los tipos de referencia](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md)

- [Destructores y finalizadores en Procedimiento: Definición y uso de clases y structs (C++/CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Operadores definidos por el usuario (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Conversiones definidas por el usuario (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Clases genéricas (C++/CLI)](generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

Consulte [Ref (Clases y structs)](../cppcx/ref-classes-and-structs-c-cx.md) y [Value (Clases y structs)](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Parámetros

*base_type*<br/>
(Opcional) Un tipo base. Un tipo **ref class** o **ref struct** puede heredar de cero o más interfaces y de cero o ningún tipo **ref**. Un tipo **value class** o **value struct** solo puede heredar de cero o más interfaces.

Al declarar un objeto mediante las palabras clave **ref class** o **ref struct**, se accede al objeto mediante un manipulador a un objeto; es decir, un puntero de contador de referencia al objeto. Cuando la variable declarada se sale del ámbito, el compilador elimina automáticamente el objeto subyacente. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente un identificador del objeto.

Cuando se declara un objeto mediante las palabras clave **value class** o **value struct**, no se supervisa la duración del objeto declarado. El objeto es como cualquier otra clase o struct estándar de C++.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

En la tabla siguiente se enumeran las diferencias con la sintaxis mostrada en la sección **Todos los runtimes** que es específica de C++/CLI.

### <a name="parameters"></a>Parámetros

*base_type*<br/>
(Opcional) Un tipo base. Un tipo **ref class** o **ref struct** puede heredar de cero o más interfaces administradas y de cero o un tipo de referencia. Un tipo **value class** o **value struct** solo se puede heredar de cero o más interfaces administradas.

Las palabras clave **ref class** y **ref struct** indican al compilador que la clase o estructura se va a asignar en el montón. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente una referencia al objeto.

Las palabras clave **value class** y **value struct** indican al compilador que el valor de la clase o de la estructura asignada se pasa a funciones o se almacena en miembros.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)