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
ms.openlocfilehash: 841b2e1e4ffbec87a170c45be8ad0cd0f831a0ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371896"
---
# <a name="volatile-c"></a>volatile (C++)

Calificador de tipo que puede utilizar para declarar que el hardware puede modificar un objeto en el programa.

## <a name="syntax"></a>Sintaxis

```
volatile declarator ;
```

## <a name="remarks"></a>Observaciones

Puede usar el modificador del compilador [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) para modificar cómo el compilador interpreta esta palabra clave.

Visual Studio interpreta la palabra clave **volatile** de forma diferente en función de la arquitectura de destino. Para ARM, si no se especifica ninguna opción del compilador **/volatile,** el compilador funciona como si se especificara **/volatile:iso.** Para arquitecturas distintas de ARM, si no se especifica ninguna opción del compilador **/volatile,** el compilador realiza como si se especificara **/volatile:ms;** Por lo tanto, para arquitecturas distintas de ARM, se recomienda encarecidamente especificar **/volatile:iso**y usar primitivas de sincronización explícitas e intrínsecos del compilador cuando se trata de memoria que se comparte entre subprocesos.

Puede usar el calificador **volatile** para proporcionar acceso a las ubicaciones de memoria que usan los procesos asincrónicos, como los controladores de interrupciones.

Cuando **volatile** se utiliza en una variable que también tiene la palabra clave [__restrict,](../cpp/extension-restrict.md) **volatile** tiene prioridad.

Si un miembro **struct** se marca como **volátil,** **volatile** se propaga a toda la estructura. Si una estructura no tiene una longitud que se puede copiar en la arquitectura actual mediante una instrucción, **volatile** puede perderse por completo en esa estructura.

La palabra clave **volatile** puede no tener ningún efecto en un campo si se cumple una de las siguientes condiciones:

- La longitud del campo volátil supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

- La longitud de la **estructura**que contiene el más externo, o si es un miembro de una **estructura**posiblemente anidada, supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

Aunque el procesador no reordena los accesos a memoria no caché, las variables no almacenes deben marcarse como **volátiles** para garantizar que el compilador no reordene los accesos a la memoria.

Los objetos que se declaran como **volátiles** no se utilizan en determinadas optimizaciones porque sus valores pueden cambiar en cualquier momento.  El sistema lee siempre el valor actual de un objeto volátil cuando se solicita, incluso aunque una instrucción anterior pidiera un valor del mismo objeto.  Además, el valor del objeto se escribe inmediatamente en la asignación.

## <a name="iso-compliant"></a>Conforme a ISO

Si está familiarizado con la palabra clave volátil de C- o está familiarizado con el comportamiento de **volatile** en versiones anteriores del compilador de Microsoft C++(MSVC), tenga en cuenta que la palabra clave **volátil** IsO Standard C++11 es diferente y se admite en MSVC cuando se especifica la opción del compilador [/volatile:iso.](../build/reference/volatile-volatile-keyword-interpretation.md) (Para ARM, se especifica de forma predeterminada). La palabra clave **volatile** en el código estándar ISO C++11 debe utilizarse únicamente para el acceso al hardware; no lo utilice para la comunicación entre subprocesos. Para la comunicación entre subprocesos, utilice mecanismos como [std::atomic\<T>](../standard-library/atomic.md) de la biblioteca estándar [C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Fin de Conforme a ISO

**Microsoft Specific**

Cuando se utiliza la opción del compilador **/volatile:ms** (de forma predeterminada cuando se dirigen a arquitecturas distintas de ARM), el compilador genera código adicional para mantener el orden entre las referencias a objetos volátiles, además de mantener el orden a las referencias a otros objetos globales. En concreto:

- Una escritura en un objeto volátil (también conocida como escritura volátil) tiene liberación de semántica; es decir, una referencia a un objeto global o estático que se produce antes que una escritura en un objeto volátil en la secuencia de instrucciones se realice antes que esa escritura volátil en el binario compilado.

- Una lectura de un objeto volátil (también conocida como lectura volátil) tiene adquisición de semántica; es decir, una referencia a un objeto global o estático que se produce después que una lectura de memoria volátil en la secuencia de instrucciones se realice después de esa lectura volátil en el binario compilado.

Esto permite utilizar objetos volátiles para bloqueos y liberaciones de memoria en aplicaciones multiproceso.

> [!NOTE]
> Cuando se basa en la garantía mejorada que se proporciona cuando se usa la opción del compilador **/volatile:ms,** el código no es portátil.

**END Microsoft Specific**

## <a name="see-also"></a>Consulte también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[const y volátil punteros](../cpp/const-and-volatile-pointers.md)
