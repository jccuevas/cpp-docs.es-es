---
title: __declspec
ms.date: 03/21/2019
f1_keywords:
- __declspec_cpp
- __declspec
- _declspec
helpviewer_keywords:
- __declspec keyword [C++]
ms.openlocfilehash: e0c99ea9379aa6e29096250e8bd36ce3d4f183e8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180230"
---
# <a name="__declspec"></a>__declspec

**Específicos de Microsoft**

La sintaxis de atributo extendido para especificar información de clase de almacenamiento utiliza la palabra clave **__declspec** , que especifica que una instancia de un tipo determinado se almacenará con un atributo de clase de almacenamiento específico de Microsoft que se enumera a continuación. Algunos ejemplos de otros modificadores de clase de almacenamiento son las palabras clave **static** y **extern** . Sin embargo, estas palabras clave forman parte de la especificación ANSI de los lenguajes C y C++ y, como tales no se incluyen en la sintaxis de atributo extendido. La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft a los lenguajes C y C++.

## <a name="grammar"></a>Gramática

*decl-Specifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp; **__declspec (** *Extended-decl-Modifier-SEQ* **)**

*extended-decl-modifier-seq*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub><br/>
&nbsp;&nbsp;&nbsp;&nbsp;*Extended-decl-Modifier* *Extended-decl-Modifier-SEQ*

*extended-decl-modifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**align (** *#* **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**asignar ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**asignador**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**AppDomain**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg ("** *segname* **")**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**desusado**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**naked**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**proceso**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**propiedad (** { **Get =** _get_func_name_ &#124; **, Put =** _put_func_name_ } **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Restrict**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**Spectre (nomitigación)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**thread**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**UUID ("** *ComObjectGUID* **")**

El espacio en blanco separa la secuencia de modificador de la declaración. En secciones posteriores aparecen ejemplos.

La gramática de atributos extendidos admite estos atributos de clase de almacenamiento específicos de Microsoft: [align](../cpp/align-cpp.md), [allocate](../cpp/allocate.md), [allocator](../cpp/allocator.md), [AppDomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [deprecated](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [DllImport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [Return](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md), [Process](../cpp/process.md), [Restrict](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [ Spectre](../cpp/spectre.md)y [Thread](../cpp/thread.md). También admite estos atributos de objetos COM: [Property](../cpp/property-cpp.md) y [UUID](../cpp/uuid-cpp.md).

Los atributos **code_seg**, **dllexport**, **DllImport**, **naked**, **noalias**, **nothrow**, **Property**, **Restrict**, **selectany**, **Thread**e **UUID** son propiedades solo de la declaración del objeto o la función a la que se aplican. El atributo **Thread** afecta solo a los datos y objetos. Los atributos **naked** y **Spectre** solo afectan a las funciones. Los atributos **DllImport** y **dllexport** afectan a funciones, datos y objetos. Los atributos **propiedad**, **selectany**y **UUID** afectan a los objetos com.

Por compatibilidad con versiones anteriores, **_declspec** es un sinónimo de **__declspec** a menos que se especifique la opción del compilador [/za \(deshabilitar extensiones de lenguaje)](../build/reference/za-ze-disable-language-extensions.md) .

Las palabras clave **__declspec** deben colocarse al principio de una declaración simple. El compilador omite, sin advertencia, las palabras clave de **__declspec** colocadas después de * o & y delante del identificador de variable en una declaración.

Un **__declspec** atributo especificado al principio de una declaración de tipos definidos por el usuario se aplica a la variable de ese tipo. Por ejemplo:

```cpp
__declspec(dllimport) class X {} varX;
```

En este caso, el atributo se aplica a `varX`. **__Declspec** atributo colocado después de que la palabra clave **Class** o **struct** se aplique al tipo definido por el usuario. Por ejemplo:

```cpp
class __declspec(dllimport) X {};
```

En este caso, el atributo se aplica a `X`.

La regla general para utilizar el atributo **__declspec** para las declaraciones simples es la siguiente:

*decl-Specifier-SEQ* *init-declarator-List*;

*Decl-Specifier-SEQ* debe contener, entre otras cosas, un tipo base (por ejemplo, **int**, **float**, una **definición**de tipo o un nombre de clase), una clase de almacenamiento (por ejemplo, **static**, **extern**) o la extensión **__declspec** . *Init-declarator-List* debe contener, entre otras cosas, la parte del puntero de las declaraciones. Por ejemplo:

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

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)
