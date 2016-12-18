---
title: "Herencia (C++) | Microsoft Docs"
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
  - "clases [C++], derivadas"
  - "clases derivadas"
  - "clases derivadas, acerca de las clases derivadas"
ms.assetid: 3534ca19-d9ed-4a40-be1b-b921ad0e6956
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Herencia (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En esta sección se explica cómo utilizar clases derivadas para crear programas extensibles.  
  
## Información general  
 Se pueden derivar nuevas clases de clases existentes utilizando un mecanismo denominado “herencia” \(vea la información que aparece en [Herencia simple](../cpp/single-inheritance.md)\).  Las clases que se utilizan para la derivación se conocen como "clases base" de una clase derivada determinada.  Una clase derivada se declara mediante la sintaxis siguiente:  
  
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
  
 Detrás de la etiqueta \(nombre\) de la clase, aparece un carácter de dos puntos seguido de una lista de especificaciones bases.  Las clases base designadas de esta forma deben haberse declarado previamente.  Las especificaciones base pueden contener un especificador de acceso, que es una de las palabras clave **public**, `protected` o `private`.  Estos especificadores de acceso aparecen delante del nombre de la clase base y solo se aplican a esa clase base.  Estos especificadores controlan el permiso de la clase derivada para su uso en miembros de la clase base.  Vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md) para obtener información sobre el acceso a miembros de la clase base.  Si se omite el especificador de acceso, el acceso a la base se considera `private`.  Las especificaciones base pueden contener la palabra clave **virtual** para indicar herencia virtual.  Esta palabra clave puede aparecer delante o detrás del especificador de acceso, si hay alguno.  Si se usa la herencia virtual, la clase base se conoce como clase base virtual.  Para obtener más información, vea [Clases bases virtuales](../misc/virtual-base-classes.md).  
  
 Se pueden especificar varias clases base, separadas por comas.  Si se especifica una sola clase base, el modelo de herencia es [Herencia simple](../cpp/single-inheritance.md). Si se especifica más de una clase base, el modelo de herencia se denomina [Herencia múltiple](http://msdn.microsoft.com/es-es/3b74185e-2beb-4e29-8684-441e51d2a2ca).  
  
 Se incluyen los temas siguientes:  
  
-   [Herencia única](../cpp/single-inheritance.md)  
  
-   [Herencia múltiple](http://msdn.microsoft.com/es-es/3b74185e-2beb-4e29-8684-441e51d2a2ca)  
  
-   [Varias clases base](../cpp/multiple-base-classes.md)  
  
-   [Clases base virtuales](../misc/virtual-base-classes.md)  
  
-   [Funciones virtuales](../cpp/virtual-functions.md)  
  
-   [Invalidaciones explícitas](../cpp/explicit-overrides-cpp.md)  
  
-   [Clases abstractas](../cpp/abstract-classes-cpp.md)  
  
-   [Resumen de reglas de ámbito](../cpp/summary-of-scope-rules.md)  
  
 Las palabras clave [\_\_super](../cpp/super.md) e [\_\_interface](../cpp/interface.md) se documentan en esta sección.  
  
## Vea también  
 [Referencia de lenguaje C\+\+](../cpp/cpp-language-reference.md)