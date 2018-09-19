---
title: Conversión Boxing implícita de tipos de valor | Documentos de Microsoft
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
ms.openlocfilehash: f1f5a455333e5cb40b63d5a5237b2df053cef194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132224"
---
# <a name="implicit-boxing-of-value-types"></a>Conversión boxing implícita de los tipos de valor
La conversión boxing de tipos de valor ha cambiado de extensiones administradas para C++ a Visual C++.  
  
 En el diseño del lenguaje, se impone una posición filosófica sobre la experiencia práctica con la característica y, en la práctica, lo cual fue un error. Como una analogía, en la versión original varios diseño del lenguaje de herencia, Stroustrup decidió que no se pudo inicializar un subobjeto de clase base virtual dentro de un constructor de clase derivada y, por lo tanto, el lenguaje requería cualquier clase que actúa como base virtual clase debe definir un constructor predeterminado. Es el constructor predeterminado que sería invocado por cualquier derivación virtual subsiguiente.  
  
 El problema de una jerarquía de clase base virtual es que la responsabilidad de la inicialización del subobjeto virtual compartido cambia con cada derivación subsiguiente. Por ejemplo, si define una clase base para que la inicialización requiere la asignación de un búfer, el tamaño especificado por el usuario de dicho búfer podría pasarse como argumento al constructor. Si, a continuación, proporcionan dos derivaciones virtuales subsiguientes, llamarlos `inputb` y `outputb`, cada una proporciona un valor determinado al constructor de clase base. Ahora, cuando deriva un `in_out` clase a partir de ambos `inputb` y `outputb`, ninguno de estos valores con el subobjeto de clase base virtual compartido manera se permita a evaluar.  
  
 Por lo tanto, en el diseño del lenguaje original, Stroustrup prohibía la inicialización explícita de una clase base virtual dentro de la lista de inicialización de miembros del constructor de clase derivada. Aunque esto resuelve el problema, en la práctica la incapacidad de dirigir la inicialización de la clase base virtual se demostró impracticable. Keith Gorlen del Instituto nacional de salud, que se implementó en una versión de software gratuito de la biblioteca de colección SmallTalk denominada nihcl, fue una voz principio en convencer a Stroustrup que tenía para tener acceso a un diseño del lenguaje más flexible.  
  
 Un principio de diseño jerárquico orientado a objetos mantiene que una clase derivada debe ocuparse solo la implementación no privada de sus clases base inmediatas. Para admitir un diseño de inicialización flexible para la herencia virtual, Stroustrup tenía que infringir este principio. La clase más derivada en una jerarquía asume la responsabilidad de toda la inicialización del subobjeto virtual sin tener en cuenta la profundidad en la jerarquía se produce. Por ejemplo, `inputb` y `outputb` son ambos responsables de inicializar explícitamente su clase base virtual inmediata. Cuando `in_out` deriva de ambos `inputb` y `outputb`, `in_out` pasa a ser responsable de la inicialización de una vez quitado la clase base virtual y realiza la inicialización de forma explícita en `inputb` y `outputb` es Suprimir.  
  
 Esto proporciona la flexibilidad necesaria por los desarrolladores de lenguajes, pero a costa de un semántica complicada. Esta serie de complicaciones se elimina si se restringe una clase base virtual que se van sin estado y simplemente permitir que se especifique una interfaz. Se trata de una expresión de diseño recomendado dentro de C++. Dentro de la programación con CLR, se eleva a directiva con el tipo de interfaz.  
  
 Este es un ejemplo de código sencillo - y en este caso, es necesaria la conversión boxing explícita:  
  
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
 [Tipos de valor y sus comportamientos (C++ / CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)