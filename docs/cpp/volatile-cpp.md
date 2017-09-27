---
title: volatile (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- volatile_cpp
- volatile
dev_langs:
- C++
helpviewer_keywords:
- interrupt handlers and volatile keyword
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
caps.latest.revision: 43
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 1bbbceaa8f170ad8c75173d60d38e5dd3df1fbdd
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="volatile-c"></a>volatile (C++)
Calificador de tipo que puede utilizar para declarar que el hardware puede modificar un objeto en el programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
volatile declarator ;  
```  
  
## <a name="remarks"></a>Comentarios  
 Puede usar el [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) modificador del compilador para modificar el modo en que el compilador interpreta esta palabra clave.  
  
 Visual Studio interpreta la palabra clave `volatile` de manera diferente según la arquitectura de destino. Para ARM, si no hay ningún **/volatile** se especifica la opción del compilador, el compilador funciona como si **/volatile:iso** se especificaron. Para las arquitecturas que no sean ARM, si no hay ningún **/volatile** se especifica la opción del compilador, el compilador funciona como si **/volatile:ms** se especificaron; por lo tanto, para crear arquitecturas de distinta de ARM se recomienda Recomendamos que especifique **/volatile:iso**y utilizar tipos primitivos de sincronización explícita e intrínsecos del compilador al tratar con memoria que se comparte entre distintos subprocesos.  
  
 Se puede utilizar el calificador `volatile` para proporcionar acceso a ubicaciones de memoria utilizadas por procesos asincrónicos como controladores de interrupciones.  
  
 Cuando `volatile` se utiliza en una variable que tiene también la [__restrict](../cpp/extension-restrict.md) palabra clave, `volatile` tiene prioridad.  
  
 Si un miembro `struct` está marcado como `volatile`, `volatile` se propaga a toda la estructura. Si una estructura no tiene una longitud que se pueda copiar en la arquitectura actual mediante una instrucción, se puede perder completamente `volatile` en esa estructura.  
  
 La palabra clave `volatile` puede no tener ningún efecto sobre un campo si se cumple una de las condiciones siguientes:  
  
-   La longitud del campo volátil supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.  
  
-   La longitud del `struct` contenedor exterior, o si es miembro de un `struct` posiblemente anidado, supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.  
  
 Aunque el procesador no reordena los accesos a memoria que no pueden almacenarse en la memoria caché, las variables que no pueden almacenarse en la memoria caché deben marcarse como `volatile` para garantizar que el compilador no reordene los accesos a memoria.  
  
 Los objetos declarados como `volatile` no se utilizan en ciertas optimizaciones porque sus valores pueden cambiar en cualquier momento.  El sistema lee siempre el valor actual de un objeto volátil cuando se solicita, incluso aunque una instrucción anterior pidiera un valor del mismo objeto.  Además, el valor del objeto se escribe inmediatamente en la asignación.  
  
## <a name="iso-compliant"></a>Conforme a ISO  
 Si está familiarizado con la C# palabra clave volatile o familiarizado con el comportamiento de `volatile` en versiones anteriores de Visual C++, tenga en cuenta que el estándar C ++ 11 ISO `volatile` palabra clave es diferente y se admite en Visual Studio cuando el [/ volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md) se especifica la opción del compilador. (Para ARM, se especifica de forma predeterminada). La palabra clave `volatile` en código del estándar C++11 de ISO se usa únicamente para el acceso de hardware; no la utilice para la comunicación entre subprocesos. Para la comunicación entre subprocesos, use mecanismos como [std:: atomic\<T >](../standard-library/atomic.md) desde el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md).  
  
## <a name="end-of-iso-compliant"></a>Fin de Conforme a ISO  
  
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Cuando el **/volatile:ms** se utiliza la opción del compilador: de forma predeterminada cuando el destinan arquitecturas que no sean ARM, el compilador genera código adicional para mantener el orden entre las referencias a objetos volátiles y orden de las referencias a otros objetos globales. En concreto:  
  
-   Una escritura en un objeto volátil (también conocida como escritura volátil) tiene liberación de semántica; es decir, una referencia a un objeto global o estático que se produce antes que una escritura en un objeto volátil en la secuencia de instrucciones se realice antes que esa escritura volátil en el binario compilado.  
  
-   Una lectura de un objeto volátil (también conocida como lectura volátil) tiene adquisición de semántica; es decir, una referencia a un objeto global o estático que se produce después que una lectura de memoria volátil en la secuencia de instrucciones se realice después de esa lectura volátil en el binario compilado.  
  
 Esto permite utilizar objetos volátiles para bloqueos y liberaciones de memoria en aplicaciones multiproceso.  
  
> [!NOTE]
>  Cuando se basa en la seguridad mejorada que se proporciona cuando el **/volatile:ms** se utiliza la opción del compilador, el código es no portable.  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Palabras clave](../cpp/keywords-cpp.md)   
 [const](../cpp/const-cpp.md)   
 [Punteros const y volatile](../cpp/const-and-volatile-pointers.md)
