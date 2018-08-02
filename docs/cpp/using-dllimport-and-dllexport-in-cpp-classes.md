---
title: Usar dllimport y dllexport en las clases de C++ | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe1454ee615f489190ec455adabcd4bdecb4e0f0
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/02/2018
ms.locfileid: "39460825"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Utilizar dllimport y dllexport en las clases de C++
## <a name="microsoft-specific"></a>Específicos de Microsoft  
 Puede declarar clases de C++ con el **dllimport** o **dllexport** atributo. Estas formas implican que se importa o exporta la clase completa. Las clases exportadas de esta forma se denominan clases exportables.  
  
 En el ejemplo siguiente se define una clase exportable. Se exportan todas sus funciones miembro y todos sus datos estáticos:  
  
```cpp 
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Tenga en cuenta que el uso explícito de la **dllimport** y **dllexport** está prohibido atributos en los miembros de una clase exportable.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a> dllexport (clases)  
 Cuando se declara una clase **dllexport**, se exportan todas sus funciones miembro y miembros de datos estáticos. Debe proporcionar las definiciones de todos esos miembros en el mismo programa. De los contrario, se genera un error del vinculador. La única excepción a esta regla afecta a las funciones virtuales puras, para las que no es necesario proporcionar definiciones explícitas. Sin embargo, dado que a un destructor de una clase abstracta siempre lo invoca el destructor de la clase base, los destructores virtuales puros deben proporcionar siempre una definición. Observe que estas reglas son las mismas para las clases no exportables.  
  
 Si exporta datos de tipo de clase o funciones que devuelven clases, asegúrese de exportar la clase.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a> DllImport (clases)  
 Cuando se declara una clase **dllimport**, se importan todas sus funciones miembro y miembros de datos estáticos. A diferencia del comportamiento de **dllimport** y **dllexport** en los tipos, miembros de datos estáticos no pueden especificar una definición en el mismo programa en el que un **dllimport** es de clase definido.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a> Clases exportables y herencia  
 Todas las clases base de una clase exportable deben ser exportables. De no ser así, se genera una advertencia del compilador. Además, todos los miembros accesibles que también son clases deben ser exportables. Esta regla permite un **dllexport** herede de un **dllimport** (clase) y un **dllimport** herede de un **dllexport** la clase (aunque este último no se recomienda). Como norma, todo lo que es accesible al cliente de la DLL (de acuerdo con las reglas de acceso de C++) debe formar parte de la interfaz exportable. En esto se incluye a los miembros de datos privados a que se hace referencia en funciones insertadas.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a> Importación/exportación selectiva de miembros  
 Dado que las funciones miembro y datos estáticos dentro de una clase implícitamente tienen vinculación externa, puede declararlos con el **dllimport** o **dllexport** atributo, a menos que se exporta la clase completa. Si la clase completa se importan o exportan, la declaración explícita de las funciones miembro y los datos como **dllimport** o **dllexport** está prohibido. Si declara un miembro de datos estáticos dentro de una definición de clase como **dllexport**, debe producirse una definición en algún lugar dentro del mismo programa (como ocurre con vinculación externa de utilizaban).  
  
 De forma similar, se puede declarar funciones miembro con el **dllimport** o **dllexport** atributos. En este caso, debe proporcionar un **dllexport** definición en algún lugar dentro del mismo programa.  
  
 Merece la pena comentar varios aspectos importantes con respecto a la importación y exportación selectiva de miembros:  
  
-   La importación/exportación selectiva de miembros sirve para proporcionar una versión de la interfaz de clase exportada que es más restrictiva; es decir, una para la que se puede diseñar una DLL que expone menos características públicas y privadas que las que el lenguaje permitiría de otra manera. También es útil para ajustar la interfaz exportable: cuando se sabe que el cliente, por definición, no puede tener acceso a algunos datos privados, no es necesario exportar toda la clase.  
  
-   Si exporta una función virtual de una clase, debe exportarlas todas, o al menos proporcionar versiones que el cliente pueda utilizar directamente.  
  
-   Si tiene una clase en la que está utilizando la importación/exportación selectiva de miembros con funciones virtuales, las funciones deben estar en la interfaz exportable o estar definidas insertadas (visibles al cliente).  
  
-   Si se define un miembro como **dllexport** pero no incluirlo en la definición de clase, se genera un error del compilador. Debe definir el miembro en el encabezado de clase.  
  
-   Aunque la definición de miembros de clase como **dllimport** o **dllexport** está permitido, no se puede invalidar la interfaz especificada en la definición de clase.  
  
-   Si define una función miembro en un lugar distinto del cuerpo de la definición de clase en que se declaró, se genera una advertencia si la función se define como **dllexport** o **dllimport** (si este definición difiere de que especificó en la declaración de clase).  
  
**FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)