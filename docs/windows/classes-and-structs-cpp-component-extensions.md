---
title: Clases y Structs (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ref class keyword [C++]
- value class keyword [C++]
- value struct keyword [C++]
- ref struct keyword [C++]
ms.assetid: 5c360764-b229-49c6-9357-66213afbc372
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 60e388e18e6d3607dac1946c3fd9a511e948afd4
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46448381"
---
# <a name="classes-and-structs--c-component-extensions"></a>Clases y structs (Extensiones de componentes de C++)

Declara una clase o struct cuya *duración del objeto* se administra automáticamente. Cuando el objeto ya no es accesible o se sale del ámbito, Visual C++ descarta automáticamente la memoria asignada al objeto.

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
(Opcional) La accesibilidad de la clase o struct fuera del ensamblado. Los valores posibles son **pública** y **privada** (**privada** es el valor predeterminado). Las clases anidadas o las estructuras no pueden tener un *class_access* especificador.

*name*<br/>
Nombre de la clase o struct.

*Modificador*<br/>
(Opcional) [abstracta](../windows/abstract-cpp-component-extensions.md) y [sealed](../windows/sealed-cpp-component-extensions.md) son modificadores válidos.

*inherit_access*<br/>
(Opcional) La accesibilidad de *base_type*. La única accesibilidad permitida es **pública** (**pública** es el valor predeterminado).

*base_type*<br/>
(Opcional) Un tipo base. Sin embargo, un tipo de valor no puede actuar como tipo base.

Para obtener más información, consulte las descripciones específicas del idioma de este parámetro en el tiempo de ejecución de Windows y Runtimesections de lenguaje común.

### <a name="remarks"></a>Comentarios

La accesibilidad del miembro predeterminado de un objeto declarado con **clase ref** o **clase de valor** es **privada**. Y la accesibilidad de miembro predeterminado de un objeto declarado con **ref struct** o **struct de valor** es **pública**.

Cuando un tipo de referencia se hereda de otro tipo de referencia, las funciones virtuales de la clase base deben reemplazarse explícitamente (con [invalidar](../windows/override-cpp-component-extensions.md)) u oculto (con [new (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). También se deben marcar explícitamente las funciones de la clase derivada como **virtual**.

Para detectar en tiempo de compilación si un tipo es un **clase ref** o **ref struct**, o un **clase de valor** o **struct de valor**, utilice `__is_ref_class (type)`, `__is_value_class (type)`, o `__is_simple_value_class (type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).

Para obtener más información sobre clases y structs, vea

- [Crear instancias de clases y Structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)

- [Semántica de pila de C++ para los tipos de referencia](../dotnet/cpp-stack-semantics-for-reference-types.md)

- [Las clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md)

- [Destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / c++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)

- [Operadores definidos por el usuario (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)

- [Conversiones definidas por el usuario (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)

- [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)

- [Clases genéricas (C++/CLI)](../windows/generic-classes-cpp-cli.md)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

Consulte [clases y structs Ref](../cppcx/ref-classes-and-structs-c-cx.md) y [clases y structs de valor](https://msdn.microsoft.com/library/windows/apps/hh699861.aspx).

### <a name="parameters"></a>Parámetros

*base_type*<br/>
(Opcional) Un tipo base. Un **clase ref** o **ref struct** puede heredar de cero o más interfaces y cero o uno **ref** tipos. Un **clase de valor** o **struct de valor** sólo puede heredar de cero o más interfaces.

Cuando declara un objeto mediante el uso de la **clase ref** o **ref struct** palabras clave, se obtiene acceso al objeto mediante un identificador de objeto; es decir, un puntero de contador de referencias al objeto. Cuando la variable declarada se sale del ámbito, el compilador elimina automáticamente el objeto subyacente. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente un identificador del objeto.

Cuando declara un objeto mediante el uso de la **clase de valor** o **struct de valor** palabras clave, la duración del objeto del objeto declarado no está supervisada. El objeto es como cualquier otra clase o struct estándar de C++.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

### <a name="remarks"></a>Comentarios

En la tabla siguiente enumera las diferencias con la sintaxis mostrada en el **todos los Runtimes** sección que son específicas de C / c++ / CLI.

### <a name="parameters"></a>Parámetros

*base_type*<br/>
(Opcional) Un tipo base. Un **clase ref** o **ref struct** puede heredar de cero o más administrados, interfaces y cero o un tipo ref. Un **clase de valor** o **struct de valor** sólo puede heredar de cero o más interfaces administradas.

El **clase ref** y **ref struct** palabras clave indican al compilador que es la clase o estructura debe asignarse en el montón. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente una referencia al objeto.

El **clase de valor** y **struct de valor** palabras clave indica al compilador que el valor de la clase o estructura asignada se pasa a funciones o almacenado en los miembros.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)