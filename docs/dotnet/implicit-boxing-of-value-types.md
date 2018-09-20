---
title: Conversión Boxing implícita de tipos de valor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387593"
---
# <a name="implicit-boxing-of-value-types"></a>Conversión boxing implícita de los tipos de valor

La conversión boxing de tipos de valor ha cambiado de extensiones administradas para C++ a Visual C++.

En el diseño del lenguaje, se impone una posición filosófica sobre la experiencia práctica con la característica y, en la práctica, era un error. De manera análoga, en el original varios diseño del lenguaje de herencia, Stroustrup decidió que no se pudo inicializar un objeto secundario de la clase base virtual dentro de un constructor de clase derivada y, por lo tanto, el lenguaje requiere cualquier clase que actúa como una base virtual clase debe definir un constructor predeterminado. Es el constructor predeterminado que se invocaría cualquier derivación virtual subsiguiente.

El problema de una jerarquía de clases base virtuales es que la responsabilidad de la inicialización del subobjeto virtual compartido cambia con cada derivación subsiguiente. Por ejemplo, si se define una clase base para cuya inicialización requiere la asignación de un búfer, el tamaño especificado por el usuario de ese búfer podría pasarse como argumento al constructor. Si, a continuación, proporcionan dos derivaciones virtuales subsiguientes, llamarlos `inputb` y `outputb`, cada una proporciona un valor determinado al constructor de clase base. Ahora, cuando deriva un `in_out` clase tanto `inputb` y `outputb`, ninguno de esos valores para el subobjeto de clase base virtual compartido puede permitir forma razonable para evaluar.

Por lo tanto, en el diseño del lenguaje original, Stroustrup no permite la inicialización explícita de una clase base virtual dentro de la lista de inicialización de miembros del constructor de clase derivada. Aunque esto resuelve el problema, en la práctica la incapacidad para dirigir la inicialización de la clase base virtual demostró impracticable. Keith Gorlen del Instituto nacional de salud, que implementó una versión de software gratuito de la biblioteca de colección SmallTalk denominada nihcl, fue el de convencer a Stroustrup que tenía que proponer un diseño más flexible del lenguaje.

Un principio de diseño jerárquico orientado a objetos contiene una clase derivada debe preocuparse solo con la implementación no privados de sus clases base inmediatas. Para admitir un diseño flexible de inicialización para la herencia virtual, Stroustrup tenía que infringir este principio. La clase más derivada en una jerarquía asume la responsabilidad de toda la inicialización del subobjeto virtual independientemente de profundidad en la jerarquía se produce. Por ejemplo, `inputb` y `outputb` son ambos responsable de inicializar explícitamente su clase base virtual inmediata. Cuando `in_out` se deriva de ambos `inputb` y `outputb`, `in_out` pasa a ser responsable de la inicialización de una vez quitado la clase base virtual y la inicialización realizado explícita en `inputb` y `outputb` es Suprimir.

Esto proporciona la flexibilidad necesaria de los desarrolladores de lenguajes, pero a costa de una semántica complicada. Esta serie de complicaciones se elimina si se restringe a una clase base virtual para ser sin estado y simplemente permitir que se especifique una interfaz. Se trata de una expresión de diseño recomendado dentro de C++. Dentro de la programación con CLR, se genera para la directiva con el tipo de interfaz.

Este es un ejemplo de código simple - y en este caso, la conversión boxing explícita no es necesario:

```
// Managed Extensions for C++ requires explicit __box operation
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };
Object* myObjArray __gc[] = {
   __box(26), __box(27), __box(28), __box(29), __box(30)
};

Console::WriteLine( "{0}\t{1}\t{2}", __box(0),
   __box(my1DIntArray->GetLowerBound(0)),
   __box(my1DIntArray->GetUpperBound(0)) );
```

Como puede ver, hay una gran cantidad de conversión boxing en curso. Tipo de valor en Visual C++, la conversión boxing es implícita:

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>Vea también

[Tipos de valor y su comportamiento (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Conversión boxing](../windows/boxing-cpp-component-extensions.md)