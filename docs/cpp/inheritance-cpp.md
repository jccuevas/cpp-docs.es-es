---
title: Herencia (C++) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- derived classes [C++]
- derived classes [C++], about derived classes
- classes [C++], derived
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: decef38bc69ea2b9a45005627b984c1f240afe13
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="inheritance--c"></a>Herencia (C++)
En esta sección se explica cómo utilizar clases derivadas para crear programas extensibles.  
  
## <a name="overview"></a>Información general  
 Pueden derivar nuevas clases de clases existentes utilizando un mecanismo denominado "herencia" (consulte la información que aparece en [herencia única](../cpp/single-inheritance.md)). Las clases que se utilizan para la derivación se conocen como "clases base" de una clase derivada determinada. Una clase derivada se declara mediante la sintaxis siguiente:  
  
```  
 class Derived : [virtual] [access-specifier] Base  
{  
   // member list  
};  
 class Derived : [virtual] [access-specifier] Base1,  
 [virtual] [access-specifier] Base2, . . .  
{  
   // member list  
};  
```  
  
 Detrás de la etiqueta (nombre) de la clase, aparece un carácter de dos puntos seguido de una lista de especificaciones bases.  Las clases base designadas de esta forma deben haberse declarado previamente.  Las especificaciones base pueden contener un especificador de acceso, que es una de las palabras clave **público**, `protected` o `private`.  Estos especificadores de acceso aparecen delante del nombre de la clase base y solo se aplican a esa clase base.  Estos especificadores controlan el permiso de la clase derivada para su uso en miembros de la clase base.  Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener información sobre el acceso a miembros de clase base.  Si se omite el especificador de acceso, el acceso a la base se considera `private`.  Las especificaciones base pueden contener la palabra clave **virtuales** para indicar herencia virtual.  Esta palabra clave puede aparecer delante o detrás del especificador de acceso, si hay alguno.  Si se usa la herencia virtual, la clase base se conoce como clase base virtual.  
  
 Se pueden especificar varias clases base, separadas por comas.  Si se especifica una sola clase base, el modelo de herencia es [único herencia](../cpp/single-inheritance.md). Si se especifica más de una clase base, el modelo de herencia se denomina [herencia múltiple](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca),  
  
 Se incluyen los temas siguientes:  
  
-   [Herencia única](../cpp/single-inheritance.md)  
  
-   [Herencia múltiple](http://msdn.microsoft.com/en-us/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [Varias clases base](../cpp/multiple-base-classes.md)  
  
-   [Funciones virtuales](../cpp/virtual-functions.md)  
  
-   [Invalidaciones explícitas](../cpp/explicit-overrides-cpp.md)  
  
-   [Clases abstractas](../cpp/abstract-classes-cpp.md)  
  
-   [Resumen de reglas de ámbito](../cpp/summary-of-scope-rules.md)  
  
 El [__super](../cpp/super.md) y [__interface](../cpp/interface.md) palabras clave se documenta en esta sección.  
  
## <a name="see-also"></a>Vea también  
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)