---
title: "Funciones virtuales privadas | Microsoft Docs"
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
  - "modificadores de acceso [C++], para los miembros de clase"
  - "clases derivadas, funciones virtuales"
  - "acceso a miembros [C++], miembros virtuales"
  - "funciones virtuales, private"
ms.assetid: 04448086-bf72-44be-9c1f-dfda1744949e
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones virtuales privadas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La manera en que se controlan las funciones virtuales privadas en clases derivadas ha cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 En Extensiones administradas, el nivel de acceso de una función virtual no restringe su capacidad para ser reemplazada dentro de una clase derivada.  En la nueva sintaxis, una función virtual no puede reemplazar a una función virtual de clase base a la que no puede tener acceso.  Por ejemplo:  
  
```  
__gc class MyBaseClass {  
   // inaccessible to a derived class   
   virtual void g();  
};  
  
__gc class MyDerivedClass : public MyBaseClass {  
public:  
   // okay in Managed Extensions; g() overrides MyBaseClass::g()  
   // error in new syntax; cannot override: MyBaseClass::g() is inaccessible …  
   void g();  
};  
```  
  
 No hay ninguna asignación real de este tipo de diseño a la nueva sintaxis.  Se debe permitir simplemente el acceso a los miembros de clase base, es decir que no sean privados.  Los métodos heredados no tienen que soportar el mismo acceso.  En este ejemplo, el cambio menos invasivo es establecer el miembro MyBaseClass como `protected`.  De este modo, el acceso del programa general al método mediante MyBaseClass sigue estando prohibido.  
  
```  
ref class MyBaseClass {  
protected:  
   virtual void g();  
};  
  
ref class MyDerivedClass : MyBaseClass {  
public:  
   virtual void g() override;  
};  
```  
  
 Observe que la ausencia de la palabra clave `virtual` explícita en la clase base, en la nueva sintaxis, genera un mensaje de advertencia.  
  
## Vea también  
 [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md)   
 [Visibilidad de miembros](../misc/member-visibility.md)