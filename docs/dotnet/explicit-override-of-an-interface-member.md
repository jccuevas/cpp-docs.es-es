---
title: "Reemplazo expl&#237;cito de un miembro de interfaz | Microsoft Docs"
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
  - "reemplazo explícito de una función virtual"
  - "funciones [C++], reemplazar"
  - "miembros de interfaz, reemplazos explícitos"
  - "reemplazar funciones"
  - "funciones virtuales, reemplazos explícitos"
ms.assetid: 46f1f536-bf43-4311-9a17-ff2282e528a9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reemplazo expl&#237;cito de un miembro de interfaz
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis para declarar un reemplazo explícito de un miembro de interfaz dentro de una clase ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Es muy frecuente que se deseen proporcionar dos instancias de un miembro de interfaz dentro de una clase que implementa la interfaz: una que se utiliza cuando se manipulan objetos de clase mediante un identificador de interfaz y otra que se utiliza cuando se usan objetos de clase mediante la interfaz de clase.  Por ejemplo:  
  
```  
public __gc class R : public ICloneable {  
   // to be used through ICloneable  
   Object* ICloneable::Clone();  
  
   // to be used through an R  
   R* Clone();  
};  
```  
  
 En Extensiones administradas esto se hace proporcionando una declaración explícita del método de la interfaz con el nombre completo del método con el nombre de la interfaz.  La instancia específica de la clase está incompleta.  Esto elimina la necesidad de convertir en un tipo inferior el valor devuelto de `Clone`, en este ejemplo, cuando se le llama explícitamente mediante una instancia de `R`.  
  
 En la nueva sintaxis, se ha introducido un mecanismo de reemplazo general que reemplaza la sintaxis de Extensiones administradas.  Nuestro ejemplo se reescribiría del modo siguiente:  
  
```  
public ref class R : public ICloneable {  
public:  
   // to be used through ICloneable  
   virtual Object^ InterfaceClone() = ICloneable::Clone;  
  
   // to be used through an R  
   virtual R^ Clone();  
};  
```  
  
 Esta revisión requiere que el miembro de interfaz que se está reemplazando explícitamente tenga un nombre único dentro de la clase.  En este ejemplo, se ha proporcionado un nombre simple como `InterfaceClone`.  El comportamiento sigue siendo el mismo: una invocación a través de la interfaz `ICloneable` invoca `InterfaceClone,` con un nuevo nombre a la vez que una llamada a través de un objeto de tipo `R` invoca la segunda instancia `Clone`.  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Invalidaciones explícitas](../windows/explicit-overrides-cpp-component-extensions.md)