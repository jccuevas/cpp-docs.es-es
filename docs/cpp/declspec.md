---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e924f3e4a038f900e084dbf84d85430d815c8e8f
ms.sourcegitcommit: 0064d37467f958dd6a5111f20d7660eaccd53ee9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416954"
---
# <a name="declspec"></a>__declspec

**Específicos de Microsoft**

La sintaxis de atributo extendido para especificar información de clase de almacenamiento utiliza la **__declspec** palabra clave, que especifica que una instancia de un tipo determinado se debe almacenar con un atributo de clase de almacenamiento específico de Microsoft enumerado a continuación. Ejemplos de otros modificadores de clase de almacenamiento la **estático** y **extern** palabras clave. Sin embargo, estas palabras clave forman parte de la especificación ANSI de los lenguajes C y C++ y, como tales no se incluyen en la sintaxis de atributo extendido. La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft a los lenguajes C y C++.

## <a name="grammar"></a>Gramática

*decl-specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**allocator**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dominio de aplicación**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**En desuso**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Proceso**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**restringir**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre(nomitigation)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**

El espacio en blanco separa la secuencia de modificador de la declaración. En secciones posteriores aparecen ejemplos.

Estos atributos de clase de almacenamiento específico de Microsoft admite la gramática de atributo extendido: [alinear](../cpp/align-cpp.md), [asignar](../cpp/allocate.md), [asignador](../cpp/allocator.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [en desuso](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md), [proceso](../cpp/process.md), [restringir](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spectre](../cpp/spectre.md), y [subproceso](../cpp/thread.md). También es compatible con estos atributos de objetos COM: [propiedad](../cpp/property-cpp.md) y [uuid](../cpp/uuid-cpp.md).

El **code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **propiedad**, **restringir**, **selectany**, **subproceso**, y **uuid**los atributos de clase de almacenamiento son propiedades solo de la declaración del objeto o función a la que se aplican. El **subproceso** atributo afecta a los datos y solo los objetos. El **naked** y **spectre** atributos que afectan a las funciones solo. El **dllimport** y **dllexport** atributos que afectan a funciones, datos y objetos. El **propiedad**, **selectany**, y **uuid** atributos que afectan a los objetos COM.

Para ofrecer compatibilidad con versiones anteriores, **_declspec** es un sinónimo de **__declspec** a menos que la opción de compilador [/Za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) es especificado.

El **__declspec** palabras clave deben colocarse al principio de una declaración simple. El compilador omite, sin advertencia, las **__declspec** palabras clave con posterioridad * o & y delante del identificador en una declaración de variable.

Un **__declspec** atributo especificado al principio de una declaración de tipo definido por el usuario se aplica a la variable de ese tipo. Por ejemplo:

```cpp
__declspec(dllimport) class X {} varX;
```

En este caso, el atributo se aplica a `varX`. Un **__declspec** atributo coloca después la **clase** o **struct** palabra clave se aplica al tipo definido por el usuario. Por ejemplo:

```cpp
class __declspec(dllimport) X {};
```

En este caso, el atributo se aplica a `X`.

La regla general para utilizar el **__declspec** atributo para las declaraciones simples es como sigue:

*decl-specifier-seq* *init-declarator-list*;

El *decl-specifier-seq* , entre otras cosas, debe contener un tipo base (por ejemplo, **int**, **float**, un **typedef**, o un nombre de clase), un clase de almacenamiento (por ejemplo, **estático**, **extern**), o la **__declspec** extensión. El *init-declarator-list* debe contener, entre otras cosas, la parte de puntero de declaraciones. Por ejemplo:

```cpp
__declspec(selectany) int * pi1 = 0;   //Recommended, selectany & int both part of decl-specifier
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator
```

El código siguiente declara una variable local para el subproceso de entero y la inicializa con un valor:

```cpp
// Example of the __declspec keyword
__declspec( thread ) int tls_i = 1;
```

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)