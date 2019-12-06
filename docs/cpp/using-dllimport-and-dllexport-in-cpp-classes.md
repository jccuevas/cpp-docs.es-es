---
title: Utilizar dllimport y dllexport en las clases de C++
ms.date: 11/04/2016
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
ms.openlocfilehash: b42ba7c1a88a4de28eb3385bbf6cad068abf1944
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857234"
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Utilizar dllimport y dllexport en las clases de C++

**Específicos de Microsoft**

Puede declarar C++ clases con el atributo **DllImport** o **dllexport** . Estas formas implican que se importa o exporta la clase completa. Las clases exportadas de esta forma se denominan clases exportables.

En el ejemplo siguiente se define una clase exportable. Se exportan todas sus funciones miembro y todos sus datos estáticos:

```cpp
#define DllExport   __declspec( dllexport )

class DllExport C {
   int i;
   virtual int func( void ) { return 1; }
};
```

Tenga en cuenta que está prohibido el uso explícito de los atributos **DllImport** y **dllexport** en los miembros de una clase exportable.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>Clases dllexport

Al declarar una clase **dllexport**, se exportan todas sus funciones miembro y miembros de datos estáticos. Debe proporcionar las definiciones de todos esos miembros en el mismo programa. De los contrario, se genera un error del vinculador. La única excepción a esta regla afecta a las funciones virtuales puras, para las que no es necesario proporcionar definiciones explícitas. Sin embargo, dado que a un destructor de una clase abstracta siempre lo invoca el destructor de la clase base, los destructores virtuales puros deben proporcionar siempre una definición. Observe que estas reglas son las mismas para las clases no exportables.

Si exporta datos de tipo de clase o funciones que devuelven clases, asegúrese de exportar la clase.

##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>DllImport (clases)

Al declarar una clase **DllImport**, se importan todas sus funciones miembro y miembros de datos estáticos. A diferencia del comportamiento de **DllImport** y **dllexport** en tipos que no son de clase, los miembros de datos estáticos no pueden especificar una definición en el mismo programa en el que se define una clase **DllImport** .

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Herencia y clases exportables

Todas las clases base de una clase exportable deben ser exportables. De no ser así, se genera una advertencia del compilador. Además, todos los miembros accesibles que también son clases deben ser exportables. Esta regla permite que una clase **dllexport** herede de una clase **DllImport** y una clase **DllImport** para heredar de una clase **dllexport** (aunque no se recomienda esta última). Como norma, todo lo que es accesible al cliente de la DLL (de acuerdo con las reglas de acceso de C++) debe formar parte de la interfaz exportable. En esto se incluye a los miembros de datos privados a que se hace referencia en funciones insertadas.

##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Importación/exportación de miembro selectivo

Dado que las funciones miembro y los datos estáticos dentro de una clase tienen implícitamente una vinculación externa, puede declararlos con el atributo **DllImport** o **dllexport** , a menos que se exporte toda la clase. Si se importa o se exporta la clase completa, se prohíbe la declaración explícita de las funciones miembro y los datos como **DllImport** o **dllexport** . Si declara un miembro de datos estático dentro de una definición de clase como **dllexport**, se debe producir una definición en alguna parte dentro del mismo programa (como con la vinculación externa que no es de clase).

Del mismo modo, puede declarar funciones miembro con los atributos **DllImport** o **dllexport** . En este caso, debe proporcionar una definición **dllexport** en alguna parte dentro del mismo programa.

Merece la pena comentar varios aspectos importantes con respecto a la importación y exportación selectiva de miembros:

- La importación/exportación selectiva de miembros sirve para proporcionar una versión de la interfaz de clase exportada que es más restrictiva; es decir, una para la que se puede diseñar una DLL que expone menos características públicas y privadas que las que el lenguaje permitiría de otra manera. También es útil para ajustar la interfaz exportable: cuando se sabe que el cliente, por definición, no puede tener acceso a algunos datos privados, no es necesario exportar toda la clase.

- Si exporta una función virtual de una clase, debe exportarlas todas, o al menos proporcionar versiones que el cliente pueda utilizar directamente.

- Si tiene una clase en la que está utilizando la importación/exportación selectiva de miembros con funciones virtuales, las funciones deben estar en la interfaz exportable o estar definidas insertadas (visibles al cliente).

- Si define un miembro como **dllexport** pero no lo incluye en la definición de clase, se genera un error del compilador. Debe definir el miembro en el encabezado de clase.

- Aunque se permite la definición de miembros de clase como **DllImport** o **dllexport** , no se puede invalidar la interfaz especificada en la definición de clase.

- Si define una función miembro en un lugar distinto del cuerpo de la definición de clase en la que la declaró, se genera una advertencia si la función se define como **dllexport** o **DllImport** (si esta definición difiere de la especificada en la declaración de clase).

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[dllexport, dllimport](../cpp/dllexport-dllimport.md)