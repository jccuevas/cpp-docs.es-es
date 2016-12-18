---
title: "Gen&#233;ricos y plantillas (Visual C++) | Microsoft Docs"
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
  - "genéricos [C++], frente a plantillas"
  - "plantillas, C++"
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Gen&#233;ricos y plantillas (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Genéricos y plantillas son ambas características de lenguaje que proporcionan compatibilidad para los tipos parametrizados.  Sin embargo, son diferentes y tienen diferente utilizan.  Este tema proporciona información general sobre las muchas diferencias.  
  
 Para obtener más información, vea [Windows en tiempo de ejecución y plantillas administradas](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md) y [Información general de plantillas](../Topic/Templates%20Overview.md).  
  
## Comparar las plantillas y Genéricos  
 Diferencias clave entre genéricos y plantillas de C\+\+:  
  
-   Los genéricos son genéricos hasta que sustituyan a tipos para ellos en tiempo de ejecución.  Las plantillas se especializan en tiempo de compilación y que no son tipos todavía con parámetros en tiempo de ejecución  
  
-   Common Language Runtime admite específicamente genéricos en MSIL.  Como el runtime conoce genéricos, tipos específicos pueden ser reemplazados por los tipos genéricos para hacer referencia a un ensamblado que contenga un tipo genérico.  Las plantillas, en cambio, resuelven en tipos normales en tiempo de compilación y tipos resultantes pueden no ser especializados en otros ensamblados.  
  
-   Los genéricos especializados en dos ensamblados diferentes con los mismos argumentos de tipo son el mismo tipo.  Plantillas especializadas en dos ensamblados diferentes con los mismos argumentos de tipo se consideran por el runtime ser tipos diferentes.  
  
-   Los genéricos se representan como parte única de código ejecutable que se utiliza para todos los argumentos de tipo de referencia \(esto no es aplicable para los tipos de valor, que tienen una implementación única por tipo de valor\).  El compilador JIT conoce genéricos y optimizar el código de referencia o tipos de valor que se utilizan como argumentos de tipo.  Las plantillas generan código independiente en tiempo de ejecución para cada especialización.  
  
-   Los genéricos no permiten el uso de parámetros de plantilla que no son de tipo, como `template <int i> C {}`.  Las plantillas los permiten.  
  
-   Los genéricos no permiten la especialización explícita \(es decir, una implementación personalizada de una plantilla para un tipo específico\).  Las plantillas hacen.  
  
-   Los genéricos no permiten la especialización parcial \(una implementación personalizada de un subconjunto de los argumentos de tipo\).  Las plantillas hacen.  
  
-   Los genéricos no permiten que el parámetro de tipo es utilizado como clase base para el tipo genérico.  Las plantillas hacen.  
  
-   Las plantillas admiten parámetros de la plantilla\- plantilla \(por ejemplo.  `template<template<class T> class X> class MyClass`\), pero los genéricos no.  
  
## Combinar las plantillas y Genéricos  
  
-   La diferencia básica sobre genéricos tiene implicaciones para compilar aplicaciones que combinan las plantillas y los genéricos.  Por ejemplo, suponga que tiene una clase de plantilla para la que desea crear un contenedor genérico para exponer esa plantilla a otros lenguajes como genérico.  No puede hacer que el genérico toma un parámetro de tipo que se pasa sin embargo a la plantilla, como plantilla debe tener ese parámetro de tipo en tiempo de compilación, pero el genérico no se resuelve el parámetro de tipo en tiempo de ejecución.  Anidar una plantilla dentro de un genérico no funcionará ya sea porque no hay manera de expandir las plantillas en tiempo de compilación para los tipos genéricos arbitrarios que pueden crearse instancias en tiempo de ejecución.  
  
## Ejemplo  
  
### Descripción  
 El ejemplo siguiente se muestra un ejemplo sencillo de plantillas mediante y de genéricos junto.  En este ejemplo, la clase de plantilla pasa el parámetro a través del tipo genérico.  El inverso no es posible.  
  
 Este lenguaje podría usar cuando desea compilar en la API genérico existente con el código de plantilla que es local a un ensamblado de Visual C\+\+, o cuando necesita agregar un nivel adicional de parametrización a un tipo genérico, aprovechar algunas características de las plantillas no admitidas por los genéricos.  
  
### Código  
  
```  
// templates_and_generics.cpp  
// compile with: /clr  
using namespace System;  
  
generic <class ItemType>  
ref class MyGeneric {  
   ItemType m_item;  
  
public:  
   MyGeneric(ItemType item) : m_item(item) {}  
   void F() {   
      Console::WriteLine("F");   
   }  
};  
  
template <class T>  
public ref class MyRef {  
MyGeneric<T>^ ig;  
  
public:  
   MyRef(T t) {  
      ig = gcnew MyGeneric<T>(t);  
      ig->F();  
    }      
};  
  
int main() {  
   // instantiate the template  
   MyRef<int>^ mref = gcnew MyRef<int>(11);  
}  
```  
  
### Resultados  
  
```  
F  
```  
  
## Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)