---
title: Clases y Structs (extensiones de componentes de C++) | Documentos de Microsoft
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
ms.openlocfilehash: 9863786e5e017b69217f984e3aa6d1db597e74d3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33864920"
---
# <a name="classes-and-structs--c-component-extensions"></a>Clases y structs (Extensiones de componentes de C++)
Declara una clase o struct cuya *duración de los objetos* se administra automáticamente. Cuando el objeto ya no es accesible o se sale del ámbito, Visual C++ descarta automáticamente la memoria asignada al objeto.  
  
## <a name="all-runtimes"></a>Todos los runtimes  
 **Sintaxis**  
  
```  
  
      class_access  
      ref class  
      name  
      modifier :  inherit_accessbase_type {};  
class_accessref structnamemodifier :  inherit_accessbase_type {};  
class_accessvalue classnamemodifier :  inherit_accessbase_type {};  
class_accessvalue structnamemodifier :  inherit_accessbase_type {};  
  
```  
  
 **Parámetros**  
  
 *class_access* (opcional)  
 La accesibilidad de la clase o struct fuera del ensamblado. Los valores posibles son **público** y `private` (`private` es el valor predeterminado). Clases anidadas o las estructuras no pueden tener un *class_access* especificador.  
  
 *name*  
 Nombre de la clase o struct.  
  
 *modificador* (opcional)  
 [abstracta](../windows/abstract-cpp-component-extensions.md) y [sellado](../windows/sealed-cpp-component-extensions.md) son modificadores válidos.  
  
 *inherit_access* (opcional)  
 Accesibilidad de `base_type`. La única accesibilidad permitida es `public` (`public` es el valor predeterminado).  
  
 *base_type* (opcional)  
 Tipo base. Sin embargo, un tipo de valor no puede actuar como tipo base.  
  
 Para obtener más información, consulte las descripciones específicas del idioma de este parámetro en el tiempo de ejecución de Windows y Runtimesections de lenguaje común.  
  
 **Comentarios**  
  
 La accesibilidad del miembro predeterminado de un objeto declarado con **clase ref** o **clase de valor** es `private`. Y la accesibilidad del miembro predeterminado de un objeto declarado con **un struct ref** o **struct de valor** es `public`.  
  
 Cuando un tipo de referencia se hereda de otro tipo de referencia, las funciones virtuales de la clase base deben reemplazarse explícitamente (con [invalidar](../windows/override-cpp-component-extensions.md)) u oculto (con [new (nueva ranura en vtable)](../windows/new-new-slot-in-vtable-cpp-component-extensions.md)). Las funciones de la clase derivada también deben marcarse explícitamente como `virtual`.  
  
 Para detectar en tiempo de compilación si un tipo es un `ref class` o `ref struct`, o un `value class` o `value struct`, use `__is_ref_class (type)`, `__is_value_class (type)`, o `__is_simple_value_class (type)`. Para obtener más información, consulte [compatibilidad de compilador para Type Traits](../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
 Para obtener más información sobre clases y structs, vea  
  
-   [Crear instancias de clases y structs](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md)  
  
 
  
-   [Semántica de pila de C++ para los tipos de referencia](../dotnet/cpp-stack-semantics-for-reference-types.md)  
  
-   [Clases, estructuras y uniones](../cpp/classes-and-structs-cpp.md)  
  
-   [Destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers)  
  
-   [Operadores definidos por el usuario (C++/CLI)](../dotnet/user-defined-operators-cpp-cli.md)  
  
-   [Conversiones definidas por el usuario (C++/CLI)](../dotnet/user-defined-conversions-cpp-cli.md)  
  
-   [Cómo: Envolver una clase nativa para usarla en C#](../dotnet/how-to-wrap-native-class-for-use-by-csharp.md)  
  
-   [Clases genéricas (C++/CLI)](../windows/generic-classes-cpp-cli.md)  
  
## <a name="windows-runtime"></a>Windows en tiempo de ejecución  
 **Comentarios**  
  
 Vea [clases y structs Ref](http://msdn.microsoft.com/library/windows/apps/hh699870.aspx) y [clases y structs de valor](http://msdn.microsoft.com/library/windows/apps/hh699861.aspx).  
  
 **Parámetros**  
  
 *base_type* (opcional)  
 Tipo base. `ref class` o `ref struct` pueden heredar de cero o más interfaces y de cero o un tipo `ref`. `value class` o `value struct` solo pueden heredar de cero o más interfaces.  
  
 Al declarar un objeto mediante las palabras clave `ref class` o `ref struct`, se obtiene acceso al objeto con un identificador de objeto, es decir, un puntero de contador de referencias al objeto. Cuando la variable declarada se sale del ámbito, el compilador elimina automáticamente el objeto subyacente. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente un identificador del objeto.  
  
 Cuando se declara un objeto mediante las palabras clave `value class` o `value struct`, la duración del objeto declarado no se supervisa. El objeto es como cualquier otra clase o struct estándar de C++.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/ZW**  
  
## <a name="common-language-runtime"></a>Common Language Runtime 
 **Comentarios**  
  
 En la tabla siguiente se enumera las diferencias con la sintaxis mostrada en el **todos los Runtimes** sección que son específicas de c++ / CLI.  
  
 **Parámetros**  
  
 *base_type* (opcional)  
 Tipo base. `ref class` o `ref struct` pueden heredar de cero o más interfaces administradas y de cero o un tipo ref. `value class` o `value struct` solo pueden heredar de cero o más interfaces administradas.  
  
 Las palabras clave `ref class` y `ref struct` indican al compilador que la clase o estructura debe asignarse en el montón. Cuando el objeto se usa como parámetro en una llamada o se almacena en una variable, se pasa o se almacena realmente una referencia al objeto.  
  
 El `value class` y `value struct` palabras clave indica al compilador que el valor de la clase o estructura asignada se pasan a las funciones o almacenado en miembros.  
  
### <a name="requirements"></a>Requisitos  
 Opción del compilador: **/clr**  
  
## <a name="see-also"></a>Vea también  
 [Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)