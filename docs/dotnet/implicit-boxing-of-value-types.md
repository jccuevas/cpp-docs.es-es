---
title: "Conversi&#243;n boxing impl&#237;cita de los tipos de valor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__box (palabra clave)"
  - "boxing (conversión)"
  - "boxing (conversión), __box (palabra clave)"
  - "boxing (conversión), Visual C++"
  - "tipos de valor, con la conversión boxing aplicada"
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversi&#243;n boxing impl&#237;cita de los tipos de valor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La conversión boxing de tipos de valor ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En el diseño del lenguaje, dimos prioridad a una posición filosófica sobre la experiencia práctica con relación a la característica, lo cual fue un error en la práctica.  Como analogía, en el diseño del lenguaje original heredado de varias fuentes, Stroustrup decidió que un subobjeto de clase base virtual no podía inicializarse dentro de un constructor de clase derivada y, por lo tanto, el lenguaje requería que cualquier clase que sirviera como clase base virtual debía definir un constructor predeterminado.  Es ese constructor predeterminado el que sería invocado por cualquier derivación virtual subsiguiente.  
  
 El problema de una jerarquía de clase base virtual es que la responsabilidad de la inicialización del subobjeto virtual compartido cambia con cada derivación subsiguiente.  Por ejemplo, si se define una clase base cuya inicialización requiere la asignación de un búfer, el tamaño especificado por el usuario de dicho búfer podría pasarse como un argumento al constructor.  A continuación, si se proporcionan dos derivaciones virtuales subsiguientes, llámense `inputb` y `outputb`, cada una proporciona un valor determinado al constructor de clase base.  Ahora, si se deriva una clase `in_out` de `inputb` y `outputb`, es prudente que se prohíba que ambos valores del subobjeto de clase base virtual compartido sean evaluados.  
  
 Por lo tanto, en el diseño del lenguaje original, Stroustrup prohibía la inicialización explícita de una clase base virtual dentro de la lista de inicialización de miembros del constructor de clase derivada.  Aunque esto resolvió el problema, en la práctica, la incapacidad de dirigir la inicialización de la clase base virtual se demostró impracticable.  Keith Gorlen del National Institute of Health \(Instituto nacional de la salud\), que implementó una versión freeware de la biblioteca de la colección SmallTalk denominada nihcl, fue el más persuasivo en convencer a Stroustrup de que tenía que encontrar un diseño del lenguaje más flexible.  
  
 Un principio de diseño jerárquico orientado a objetos mantiene que una clase derivada sólo debería ocuparse de la implementación no privada de sus clases base inmediatas.  Para admitir un diseño de inicialización flexible para la herencia virtual, Stroustrup tenía que infringir este principio.  La clase más derivada en una jerarquía asume la responsabilidad de toda la inicialización del subobjeto virtual sin tener en cuenta lo profundo que se encuentre dentro de la jerarquía.  Por ejemplo, `inputb` y `outputb` son ambos responsables de inicializar explícitamente su clase base virtual inmediata.  Si `in_out` deriva de `inputb` y de `outputb`, `in_out` se hace responsable de inicializar la clase base virtual que una vez se eliminó, y se quita la inicialización realizada de forma explícita en `inputb` y `outputb`.  
  
 Esto proporciona la flexibilidad necesaria para los desarrolladores de lenguajes, pero a costa de un semántica complicada.  Esta serie de complicaciones se puede evitar si se restringe una clase base virtual para que esté sin un estado y simplemente se le permite que especifique una interfaz.  Éste es un modismo de diseño recomendado dentro de C\+\+.  Dentro de la programación con CLR, se eleva a directiva con el tipo de interfaz.  
  
 A continuación, se muestra un ejemplo de código simple y, en este caso, la conversión boxing explícita es innecesaria:  
  
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
  
 Como puede ver, hay una extensa conversión boxing en curso.  En [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)], la conversión boxing de tipos de valor es implícita:  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## Vea también  
 [Tipos de valor y su comportamiento \(C\+\+\/CLI\)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Conversión boxing](../windows/boxing-cpp-component-extensions.md)