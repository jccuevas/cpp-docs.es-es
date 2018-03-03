---
title: __declspec | Microsoft Docs
ms.custom: 
ms.date: 1/23/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- __declspec_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++]
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 51a08092160ecb288decae343713e5a4f6e507b1
ms.sourcegitcommit: 9a0a287d6940591523af959ebdac5affa36220da
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="declspec"></a>__declspec

**Específicos de Microsoft**

La sintaxis de atributo extendido para especificar información de clase de almacenamiento usa el **__declspec** (palabra clave), que especifica que una instancia de un tipo determinado se debe almacenar con un atributo de clase de almacenamiento específicos de Microsoft enumerado a continuación. Ejemplos de otros modificadores de clase de almacenamiento incluyen el **estático** y **extern** palabras clave. Sin embargo, estas palabras clave forman parte de la especificación ANSI de los lenguajes C y C++ y, como tales no se incluyen en la sintaxis de atributo extendido. La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft a los lenguajes C y C++.

## <a name="grammar"></a>Gramática

*decl-specifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**__declspec (**  *extended-decl-modifier-seq*  **)**

*extended-decl-modifier-seq*:  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier*<sub>opt</sub>  
&nbsp;&nbsp;&nbsp;&nbsp;*extended-decl-modifier* *extended-decl-modifier-seq*

*extended-decl-modifier*:  
&nbsp;&nbsp;&nbsp;&nbsp;**align(** *#* **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**allocate("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**appdomain**  
&nbsp;&nbsp;&nbsp;&nbsp;**code_seg("** *segname* **")**  
&nbsp;&nbsp;&nbsp;&nbsp;**deprecated**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllimport**  
&nbsp;&nbsp;&nbsp;&nbsp;**dllexport**  
&nbsp;&nbsp;&nbsp;&nbsp;**jitintrinsic**  
&nbsp;&nbsp;&nbsp;&nbsp;**naked**  
&nbsp;&nbsp;&nbsp;&nbsp;**noalias**  
&nbsp;&nbsp;&nbsp;&nbsp;**noinline**  
&nbsp;&nbsp;&nbsp;&nbsp;**noreturn**  
&nbsp;&nbsp;&nbsp;&nbsp;**nothrow**  
&nbsp;&nbsp;&nbsp;&nbsp;**novtable**  
&nbsp;&nbsp;&nbsp;&nbsp;**proceso**  
&nbsp;&nbsp;&nbsp;&nbsp;**property(** { **get=**_get_func_name_ &#124; **,put=**_put_func_name_ } **)**  
&nbsp;&nbsp;&nbsp;&nbsp;**restrict**  
&nbsp;&nbsp;&nbsp;&nbsp;**safebuffers**  
&nbsp;&nbsp;&nbsp;&nbsp;**selectany**  
&nbsp;&nbsp;&nbsp;&nbsp;**spectre(nomitigation)**  
&nbsp;&nbsp;&nbsp;&nbsp;**thread**  
&nbsp;&nbsp;&nbsp;&nbsp;**uuid("** *ComObjectGUID* **")**  

El espacio en blanco separa la secuencia de modificador de la declaración. En secciones posteriores aparecen ejemplos.

Gramática de atributo extendido es compatible con estos atributos de clase de almacenamiento específicas de Microsoft: [alinear](../cpp/align-cpp.md), [asignar](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [en desuso](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [proceso](../cpp/process.md), [restringir](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), [spectre](../cpp/spectre.md), y [subproceso](../cpp/thread.md). También es compatible con estos atributos de objetos COM: [propiedad](../cpp/property-cpp.md) y [uuid](../cpp/uuid-cpp.md).

El **code_seg**, **dllexport**, **dllimport**, **naked**, **noalias**, **nothrow** , **propiedad**, **restringir**, **selectany**, **subproceso**, y **uuid**los atributos de clase de almacenamiento son propiedades solo de la declaración del objeto o función a la que se aplican. El **subproceso** atributo afecta a los datos y solo los objetos. El **naked** y **spectre** atributos que afectan a las funciones. El **dllimport** y **dllexport** atributos afectan a funciones, datos y objetos. El **propiedad**, **selectany**, y **uuid** atributos afectan a los objetos COM.

El **__declspec** palabras clave debe colocarse al principio de una declaración simple. El compilador omite, sin advertencia, las **__declspec** palabras clave colocado después * o & y delante del identificador en una declaración de variable.

A **__declspec** atributo especificado al principio de una declaración de tipo definido por el usuario se aplica a la variable de ese tipo. Por ejemplo:

```cpp
__declspec(dllimport) class X {} varX;
```

En este caso, el atributo se aplica a `varX`. A **__declspec** atributo coloca después la **clase** o **struct** palabra clave se aplica al tipo definido por el usuario. Por ejemplo:

```cpp
class __declspec(dllimport) X {};
```

En este caso, el atributo se aplica a `X`.

La regla general para utilizar el **__declspec** atributo para las declaraciones simples es como sigue:

*decl-specifier-seq* *init-declarator-list*;

El *decl-specifier-seq* , entre otras cosas, debe contener un tipo base (por ejemplo, **int**, **float**, un **typedef**, o un nombre de clase), clase de almacenamiento (por ejemplo, **estático**, **extern**), o la **__declspec** extensión. El *init-declarator-list* debe contener, entre otras cosas, la parte de puntero de declaraciones. Por ejemplo:

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

[Palabras clave](../cpp/keywords-cpp.md)  
[Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)  
