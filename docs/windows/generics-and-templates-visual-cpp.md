---
title: "Genéricos y plantillas (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- generics [C++], vs. templates
- templates, C++
ms.assetid: 63adec79-b1dc-4a1a-a21d-b8a72a8fce31
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 307cc39e64a6fd91f3f5f96da634e47d3e9a9030
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="generics-and-templates-visual-c"></a>Genéricos y plantillas (Visual C++)
Genéricos y plantillas son las características del lenguaje que proporcionan compatibilidad para tipos parametrizados. Sin embargo, son diferentes y tienen diferentes usos. Este tema proporciona información general sobre las numerosas diferencias existentes.  
  
 Para obtener más información, consulte [Windows Runtime y plantillas administradas](../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md).  
  
## <a name="comparing-templates-and-generics"></a>Comparación de plantillas y tipos genéricos  
 Diferencias principales entre genéricos y plantillas de C++:  
  
-   Los genéricos son genéricos hasta que los tipos se sustituyen por ellos en tiempo de ejecución. Plantillas están especializadas en tiempo de compilación, por lo que no son tipos parametrizados todavía en tiempo de ejecución  
  
-   Common language runtime admite específicamente genéricos en MSIL. Dado que el tiempo de ejecución sabe acerca de los genéricos, tipos específicos se pueden sustituir por tipos genéricos al hacer referencia a un ensamblado que contiene un tipo genérico. Plantillas, en cambio, resolver en los tipos normales en tiempo de compilación y los tipos resultantes no se pueden especializar de otros ensamblados.  
  
-   Los tipos genéricos especializados en ensamblados diferentes con el mismo tipo de argumentos son del mismo tipo. Plantillas especializados en ensamblados diferentes con el mismo tipo de argumentos se consideran en tiempo de ejecución son de tipos diferentes.  
  
-   Los tipos genéricos se generan como un único fragmento de código ejecutable que se utiliza para todos los argumentos de tipo de referencia (Esto no es true para los tipos de valor, que tienen una implementación por tipo de valor única). El compilador JIT sabe acerca de los genéricos y se puede optimizar el código para los tipos de valor o referencia que se utilizan como argumentos de tipo. Las plantillas de generar código en tiempo de ejecución independiente para cada especialización.  
  
-   Genéricos no permitir los parámetros de plantilla sin tipo, como `template <int i> C {}`. Las plantillas permiten a ellos.  
  
-   Los genéricos no permiten la especialización explícita (es decir, una implementación personalizada de una plantilla para un tipo específico). Plantillas de hacerlo.  
  
-   Los genéricos no permiten la especialización parcial (una implementación personalizada que va a un subconjunto de los argumentos de tipo). Plantillas de hacerlo.  
  
-   Los genéricos no permiten el parámetro de tipo que se usará como la clase base para el tipo genérico. Plantillas de hacerlo.  
  
-   Plantillas admiten parámetros de plantilla de plantilla (p. ej. `template<template<class T> class X> class MyClass`), pero no genéricos.  
  
## <a name="combining-templates-and-generics"></a>Genéricos y plantillas de combinación  
  
-   La diferencia básica en genéricos tiene implicaciones para crear aplicaciones que combinan plantillas y tipos genéricos. Por ejemplo, suponga que tiene una clase de plantilla que desea crear un contenedor genérico para exponer esa plantilla a otros lenguajes como un tipo genérico. No puede tener el genérico toman un parámetro de tipo que, a continuación, pasa directo a la plantilla, puesto que la plantilla debe tener ese parámetro de tipo en tiempo de compilación, pero la clase genérica no resolver el parámetro de tipo hasta el tiempo de ejecución. Anidar una plantilla dentro de un tipo genérico no funcionará bien porque no hay ninguna manera para expandir las plantillas en tiempo de compilación para los tipos genéricos arbitrarios que se pueden crear instancias en tiempo de ejecución.  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 En el ejemplo siguiente se muestra un ejemplo sencillo de usar plantillas y tipos genéricos juntos. En este ejemplo, la clase de plantilla pasa su parámetro a través del tipo genérico. Lo contrario no es posible.  
  
 Esta expresión podría utilizarse cuando desea compilar en una API existente genérica con un código de plantilla que es local a un ensamblado de Visual C++, o cuando necesite agregar una capa adicional de la parametrización a un tipo genérico, para aprovechar las ventajas de determinadas características de plantillas no admitidas d. por genéricos  
  
### <a name="code"></a>Código  
  
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
  
### <a name="output"></a>Salida  
  
```  
F  
```  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)