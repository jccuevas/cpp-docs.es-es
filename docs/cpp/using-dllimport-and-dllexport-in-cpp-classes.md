---
title: "Usar dllimport y dllexport en las clases de C++ | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases [C++], declarar"
  - "clases [C++], exportables y herencia"
  - "declaraciones [C++], class"
  - "declarar clases"
  - "dllexport (atributo) [C++]"
  - "dllexport (atributo) [C++], clases"
  - "dllimport (atributo) [C++], clases"
  - "clases exportables [C++]"
  - "exportar clases"
  - "herencia [C++], clases exportables"
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar dllimport y dllexport en las clases de C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Puede declarar clases de C\+\+ con el atributo **dllimport** o `dllexport`.  Estas formas implican que se importa o exporta la clase completa.  Las clases exportadas de esta forma se denominan clases exportables.  
  
 En el ejemplo siguiente se define una clase exportable.  Se exportan todas sus funciones miembro y todos sus datos estáticos:  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Observe que está prohibido el uso explícito de los atributos **dllimport** y `dllexport` en los miembros de una clase exportable.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> dllexport \(Clases\)  
 Cuando se declara una clase `dllexport`, se exportan todas sus funciones miembro y todos sus miembros de datos estáticos.  Debe proporcionar las definiciones de todos esos miembros en el mismo programa.  De los contrario, se genera un error del vinculador.  La única excepción a esta regla afecta a las funciones virtuales puras, para las que no es necesario proporcionar definiciones explícitas.  Sin embargo, dado que a un destructor de una clase abstracta siempre lo invoca el destructor de la clase base, los destructores virtuales puros deben proporcionar siempre una definición.  Observe que estas reglas son las mismas para las clases no exportables.  
  
 Si exporta datos de tipo de clase o funciones que devuelven clases, asegúrese de exportar la clase.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> dllimport \(Clases\)  
 Cuando se declara una clase **dllimport**, se importan todas sus funciones miembro y todos sus miembros de datos estáticos.  A diferencia del comportamiento de **dllimport** y `dllexport` en tipos que no son de clase, los miembros de datos estáticos no pueden especificar una definición en el mismo programa en el que se define una clase **dllimport**.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Herencia y clases exportables  
 Todas las clases base de una clase exportable deben ser exportables.  De no ser así, se genera una advertencia del compilador.  Además, todos los miembros accesibles que también son clases deben ser exportables.  Esta regla permite que una clase `dllexport` herede de una clase **dllimport** y una clase **dllimport** herede de una clase `dllexport` \(aunque esto último no se recomienda\).  Como norma, todo lo que es accesible al cliente de la DLL \(de acuerdo con las reglas de acceso de C\+\+\) debe formar parte de la interfaz exportable.  En esto se incluye a los miembros de datos privados a que se hace referencia en funciones insertadas.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Importación\/exportación selectiva de miembros  
 Debido a que las funciones miembro y los datos estáticos dentro de una clase tienen implícitamente una vinculación externa, puede declararlos con el atributo **dllimport** o `dllexport`, a menos que se exporte toda la clase.  Si se importa o se exporta la clase completa, se prohíbe la declaración explícita de funciones miembro y datos como **dllimport** o `dllexport`.  Si declara un miembro de datos estático dentro de una definición de clase como `dllexport`, debe producirse una definición en alguna parte dentro del mismo programa \(como con la vinculación externa que no es de clase\).  
  
 De igual forma, puede declarar funciones miembro con los atributos **dllimport** o `dllexport`.  En este caso, debe proporcionar una definición de `dllexport` en alguna parte dentro del mismo programa.  
  
 Merece la pena comentar varios aspectos importantes con respecto a la importación y exportación selectiva de miembros:  
  
-   La importación\/exportación selectiva de miembros sirve para proporcionar una versión de la interfaz de clase exportada que es más restrictiva; es decir, una para la que se puede diseñar una DLL que expone menos características públicas y privadas que las que el lenguaje permitiría de otra manera.  También es útil para ajustar la interfaz exportable: cuando se sabe que el cliente, por definición, no puede tener acceso a algunos datos privados, no es necesario exportar toda la clase.  
  
-   Si exporta una función virtual de una clase, debe exportarlas todas, o al menos proporcionar versiones que el cliente pueda utilizar directamente.  
  
-   Si tiene una clase en la que está utilizando la importación\/exportación selectiva de miembros con funciones virtuales, las funciones deben estar en la interfaz exportable o estar definidas insertadas \(visibles al cliente\).  
  
-   Si define un miembro como `dllexport` pero no lo incluye en la definición de clase, se genera un error del compilador.  Debe definir el miembro en el encabezado de clase.  
  
-   Aunque se permite la definición de miembros de clase como **dllimport** o `dllexport`, no se puede invalidar la interfaz especificada en la definición de clase.  
  
-   Si define una función miembro en un lugar distinto del cuerpo de la definición de clase en que se declaró, se genera una advertencia si la función se define como `dllexport` o **dllimport** \(si esta definición difiere de la especificada en la declaración de clase\).  
  
### FIN de Específicos de Microsoft  
  
## Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)