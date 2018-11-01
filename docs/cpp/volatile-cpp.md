---
title: volatile (C++)
ms.date: 11/04/2016
f1_keywords:
- volatile_cpp
helpviewer_keywords:
- interrupt handlers and volatile keyword [C++]
- volatile keyword [C++]
- volatile objects
- objects [C++], volatile
ms.assetid: 81db4a85-ed5a-4a2c-9a53-5d07a771d2de
ms.openlocfilehash: 73243841b2ad02bcc165b2910ac54283028e6cf3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50664027"
---
# <a name="volatile-c"></a>volatile (C++)

Calificador de tipo que puede utilizar para declarar que el hardware puede modificar un objeto en el programa.

## <a name="syntax"></a>Sintaxis

```
volatile declarator ;
```

## <a name="remarks"></a>Comentarios

Puede usar el [/volatile](../build/reference/volatile-volatile-keyword-interpretation.md) modificador del compilador para modificar cómo interpreta el compilador esta palabra clave.

Visual Studio interpreta la **volátil** palabra clave de manera diferente dependiendo de la arquitectura de destino. Para ARM, si no hay ningún **/volatile** se especificó la opción del compilador, el compilador funciona como si **/volatile: ISO** se han especificado. Arquitecturas que no sean ARM, si no hay ningún **/volatile** se especifica la opción del compilador, el compilador realiza como si **/volatile: MS** se especificaron; por lo tanto, para las arquitecturas distintas de ARM se fuertemente se recomienda que especifique **/volatile: ISO**y use las primitivas de sincronización explícita e intrínsecos del compilador al tratar con memoria compartida entre subprocesos.

Puede usar el **volátil** calificador para proporcionar acceso a ubicaciones de memoria que se usan por procesos asincrónicos como controladores de interrupción.

Cuando **volátil** se utiliza en una variable que tiene también la [__restrict](../cpp/extension-restrict.md) palabra clave, **volátil** tiene prioridad.

Si un **struct** miembro está marcado como **volátil**, a continuación, **volátil** se propaga a toda la estructura. Si una estructura no tiene una longitud que se puede copiar en la arquitectura actual mediante una instrucción **volátil** se puede perder completamente en esa estructura.

El **volátil** palabra clave no puede tener ningún efecto en un campo si se cumple una de las condiciones siguientes:

- La longitud del campo volátil supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

- La longitud de contenedor exterior **struct**, o si es un miembro de un posiblemente anidado **struct**, supera el tamaño máximo que se puede copiar en la arquitectura actual mediante una instrucción.

Aunque el procesador no reordenar los accesos a memoria no almacenables en caché, las variables no almacenables en caché deben marcarse como **volátil** garantizar que el compilador no reordene la memoria tiene acceso.

Los objetos que se declaran como **volátil** no se utilizan en ciertas optimizaciones porque sus valores pueden cambiar en cualquier momento.  El sistema lee siempre el valor actual de un objeto volátil cuando se solicita, incluso aunque una instrucción anterior pidiera un valor del mismo objeto.  Además, el valor del objeto se escribe inmediatamente en la asignación.

## <a name="iso-compliant"></a>Conforme a ISO

Si está familiarizado con el C# palabra clave volatile, o está familiarizado con el comportamiento de **volátil** en versiones anteriores de Visual C++, tenga en cuenta que el estándar C ++ 11 de ISO **volátil** palabra clave es diferente y es compatible con Visual Studio cuando el [/volatile: ISO](../build/reference/volatile-volatile-keyword-interpretation.md) se especificó la opción del compilador. (Para ARM, se especifica de forma predeterminada). El **volátil** palabra clave en C ++ 11 estándar ISO de código es para usarse solo para el acceso de hardware; no lo utilice para la comunicación entre subprocesos. Para la comunicación entre subprocesos, use mecanismos como [std:: atomic\<T >](../standard-library/atomic.md) desde el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md).

## <a name="end-of-iso-compliant"></a>Fin de Conforme a ISO

## <a name="microsoft-specific"></a>Específicos de Microsoft

Cuando el **/volatile: MS** se utiliza la opción del compilador: de forma predeterminada cuando tienen como destino arquitecturas que no sean ARM, el compilador genera código adicional para mantener el orden entre las referencias a objetos volátiles y orden de las referencias a otros objetos globales. En concreto:

- Una escritura en un objeto volátil (también conocida como escritura volátil) tiene liberación de semántica; es decir, una referencia a un objeto global o estático que se produce antes que una escritura en un objeto volátil en la secuencia de instrucciones se realice antes que esa escritura volátil en el binario compilado.

- Una lectura de un objeto volátil (también conocida como lectura volátil) tiene adquisición de semántica; es decir, una referencia a un objeto global o estático que se produce después que una lectura de memoria volátil en la secuencia de instrucciones se realice después de esa lectura volátil en el binario compilado.

Esto permite utilizar objetos volátiles para bloqueos y liberaciones de memoria en aplicaciones multiproceso.

> [!NOTE]
>  Cuando se basa en la seguridad mejorada que se proporciona cuando el **/volatile: MS** se utiliza la opción del compilador, el código es no portable.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Palabras clave](../cpp/keywords-cpp.md)<br/>
[const](../cpp/const-cpp.md)<br/>
[Punteros const y volatile](../cpp/const-and-volatile-pointers.md)