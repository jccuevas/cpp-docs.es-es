---
title: volatile (C++)
ms.date: 05/07/2019
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 6d193c530cbe0258d8713883b769fe4828a248c1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187432"
---
# <a name="volatile-c"></a>volatile (C++)

Calificador de tipo que puede utilizar para declarar que el hardware puede modificar un objeto en el programa.

## <a name="syntax"></a>Sintaxis

```
volatile declarator ;
```

## <a name="remarks"></a>Observaciones

Puede usar el modificador de compilador [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) para modificar el modo en que el compilador interpreta esta palabra clave.

Visual Studio interpreta la palabra clave **volatile** de forma diferente en función de la arquitectura de destino. En el caso de ARM, si no se especifica ninguna opción del compilador **/volatile** , el compilador funciona como si se hubiera especificado **/volatile: ISO** . En el caso de las arquitecturas que no sean ARM, si no se especifica ninguna opción del compilador **/volatile** , el compilador funciona como si se hubiera especificado **/volatile: MS** ; por lo tanto, para las arquitecturas que no sean ARM, se recomienda encarecidamente especificar **/volatile: ISO**y usar primitivas de sincronización explícitas y intrínsecos del compilador cuando se trabaja con memoria compartida entre subprocesos.

Puede usar el calificador **volatile** para proporcionar acceso a las ubicaciones de memoria que usan los procesos asincrónicos, como los controladores de interrupción.

Cuando **volatile** se utiliza en una variable que también tiene la palabra clave [__restrict](../cpp/extension-restrict.md) , **volatile** tiene prioridad.

Si un miembro de **struct** está marcado como **volatile**, **volatile** se propaga a toda la estructura. Si una estructura no tiene una longitud que se pueda copiar en la arquitectura actual mediante una instrucción, es posible que **volatile** se pierda por completo en esa estructura.

La palabra clave **volatile** puede no tener ningún efecto en un campo si se cumple alguna de las condiciones siguientes:

- La longitud del campo volátil supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

- La longitud de la **estructura**contenedora más externa (o si es un miembro de una **estructura**posiblemente anidada) supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

Aunque el procesador no reordena los accesos de memoria no almacenables en caché, las variables no almacenables en caché deben marcarse como **volátiles** para garantizar que el compilador no reordene los accesos de memoria.

Los objetos que se declaran como **volatile** no se usan en ciertas optimizaciones porque sus valores pueden cambiar en cualquier momento.  El sistema lee siempre el valor actual de un objeto volátil cuando se solicita, incluso aunque una instrucción anterior pidiera un valor del mismo objeto.  Además, el valor del objeto se escribe inmediatamente en la asignación.

## <a name="iso-compliant"></a>Conforme a ISO

Si está familiarizado con la C# palabra clave volatile o está familiarizado con el comportamiento de **volatile** en versiones C++ anteriores del compilador de Microsoft (MSVC), tenga en cuenta que la palabra clave **volatile** estándar ISO de C++ 11 es diferente y se admite en MSVC cuando se especifica la opción del compilador [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) . (Para ARM, se especifica de forma predeterminada). La palabra clave **volatile** del código estándar ISO de c++ 11 solo se utiliza para el acceso de hardware; no lo use para la comunicación entre subprocesos. Para la comunicación entre subprocesos, use mecanismos como [STD:: Atomic\<t >](../standard-library/atomic.md) de la [ C++ biblioteca estándar](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Fin de Conforme a ISO

**Específicos de Microsoft**

Cuando se usa la opción del compilador **/volatile: MS** (de forma predeterminada, cuando se destina a arquitecturas distintas de ARM), el compilador genera código adicional para mantener el orden entre las referencias a objetos volátiles, además de mantener el orden de las referencias a otros objetos globales. En concreto:

- Una escritura en un objeto volátil (también conocida como escritura volátil) tiene liberación de semántica; es decir, una referencia a un objeto global o estático que se produce antes que una escritura en un objeto volátil en la secuencia de instrucciones se realice antes que esa escritura volátil en el binario compilado.

- Una lectura de un objeto volátil (también conocida como lectura volátil) tiene adquisición de semántica; es decir, una referencia a un objeto global o estático que se produce después que una lectura de memoria volátil en la secuencia de instrucciones se realice después de esa lectura volátil en el binario compilado.

Esto permite utilizar objetos volátiles para bloqueos y liberaciones de memoria en aplicaciones multiproceso.

> [!NOTE]
>  Cuando se basa en la garantía mejorada que se proporciona cuando se usa la opción del compilador **/volatile: MS** , el código no es portátil.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Punteros const y volatile](../cpp/const-and-volatile-pointers.md)
