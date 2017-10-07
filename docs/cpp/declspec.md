---
title: __declspec | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
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
ms.assetid: 832db681-e8e1-41ca-b78c-cd9d265cdb87
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: b29b6243611f1ca59a579869469c803d3735f9df
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="declspec"></a>__declspec
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 La sintaxis de atributo extendido para especificar información de clase de almacenamiento utiliza la palabra clave `__declspec`, que especifica que una instancia de un tipo determinado se debe almacenar con un atributo de clase de almacenamiento específico de Microsoft que se muestra a continuación. Ejemplos de otros modificadores de clase de almacenamiento incluyen las palabras clave `static` y `extern`. Sin embargo, estas palabras clave forman parte de la especificación ANSI de los lenguajes C y C++ y, como tales no se incluyen en la sintaxis de atributo extendido. La sintaxis de atributo extendido simplifica y normaliza las extensiones específicas de Microsoft a los lenguajes C y C++.  
  
## <a name="grammar"></a>Gramática  
 *decl-specifier*:  
 `__declspec (`  *Extended-decl-modifier-seq*  `)`  
  
 *extended-decl-modifier-seq*:  
 *extended-decl-modifier*opt  
  
 *Extended-decl-modifier extended-decl-modifier-seq*  
  
 *extended-decl-modifier*:  
 `align(` *#* `)`  
  
 `allocate("`*segname*`")`  
  
 `appdomain`  
  
 `code_seg("`*segname*`")`  
  
 `deprecated`  
  
 `dllimport`  
  
 `dllexport`  
  
 `jitintrinsic`  
  
 `naked`  
  
 `noalias`  
  
 `noinline`  
  
 `noreturn`  
  
 `nothrow`  
  
 `novtable`  
  
 `process`  
  
 `property(`{`get=`*get_func_name*&#124;`,put=` *put_func_name*}`)`  
  
 `restrict`  
  
 `safebuffers`  
  
 `selectany`  
  
 `thread`  
  
 `uuid("`*ComObjectGUID*`")`  
  
 El espacio en blanco separa la secuencia de modificador de la declaración. En secciones posteriores aparecen ejemplos.  
  
 Gramática de atributo extendido es compatible con estos atributos de clase de almacenamiento específicas de Microsoft: [alinear](../cpp/align-cpp.md), [asignar](../cpp/allocate.md), [appdomain](../cpp/appdomain.md), [code_seg](../cpp/code-seg-declspec.md), [en desuso](../cpp/deprecated-cpp.md), [dllexport](../cpp/dllexport-dllimport.md), [dllimport](../cpp/dllexport-dllimport.md), [jitintrinsic](../cpp/jitintrinsic.md), [naked](../cpp/naked-cpp.md), [noalias](../cpp/noalias.md), [noinline](../cpp/noinline.md), [noreturn](../cpp/noreturn.md), [nothrow](../cpp/nothrow-cpp.md), [novtable](../cpp/novtable.md) , [proceso](../cpp/process.md), [restringir](../cpp/restrict.md), [safebuffers](../cpp/safebuffers.md), [selectany](../cpp/selectany.md), y [subproceso](../cpp/thread.md). También es compatible con estos atributos de objetos COM: [propiedad](../cpp/property-cpp.md) y [uuid](../cpp/uuid-cpp.md).  
  
 Los atributos de clase de almacenamiento `code_seg`, `dllexport`, `dllimport`, `naked`, `noalias`, `nothrow`, `property`, `restrict`, `selectany`, `thread` y `uuid` son propiedades solo de la declaración del objeto o la función a los que se aplican. El atributo `thread` solo afecta a datos y objetos. El atributo `naked` solo afecta a funciones. Los atributos `dllimport` y `dllexport` afectan a funciones, datos y objetos. Los atributos `property`, `selectany` y `uuid` afectan a objetos COM.  
  
 Las palabras clave `__declspec` deben colocarse al principio de una declaración simple. El compilador omite, sin advertencia, las palabras clave `__declspec` situadas después de * o & y delante del identificador de variable en una declaración.  
  
 Un atributo `__declspec` especificado al comienzo de una declaración de tipos definidos por el usuario se aplica a la variable de ese tipo. Por ejemplo:  
  
```  
__declspec(dllimport) class X {} varX;  
```  
  
 En este caso, el atributo se aplica a `varX`. Un atributo `__declspec` situado después de la palabra clave `class` o `struct` se aplica al tipo definido por el usuario. Por ejemplo:  
  
```  
class __declspec(dllimport) X {};  
```  
  
 En este caso, el atributo se aplica a `X`.  
  
 La regla general para utilizar el atributo `__declspec` para las declaraciones simples es la siguiente:  
  
```  
  
decl-specifier-seq  
declarator-list;  
```  
  
 El *decl-specifier-seq* , entre otras cosas, debe contener un tipo base (p. ej. `int`, `float`, `typedef`, o un nombre de clase), una clase de almacenamiento (por ejemplo, `static`, `extern`), o la `__declspec`extensión. El *init-declarator-list* debe contener, entre otras cosas, la parte de puntero de declaraciones. Por ejemplo:  
  
```  
__declspec(selectany) int * pi1 = 0;   //OK, selectany & int both part of decl-specifier  
int __declspec(selectany) * pi2 = 0;   //OK, selectany & int both part of decl-specifier  
int * __declspec(selectany) pi3 = 0;   //ERROR, selectany is not part of a declarator  
```  
  
 El código siguiente declara una variable local de subproceso de entero y la inicializa con un valor:  
  
```  
// Example of the __declspec keyword  
__declspec( thread ) int tls_i = 1;  
```  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [Atributos extendidos de clase de almacenamiento de C](../c-language/c-extended-storage-class-attributes.md)
