---
title: "Crear instancias de plantillas de funci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas de función, creación de instancias"
  - "creación de instancias, plantillas de función"
  - "plantillas, creación de instancias"
ms.assetid: f22a07c7-3ad1-465a-84f5-8737e274bd47
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Crear instancias de plantillas de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se llama por primera vez a una plantilla de función para cada tipo, el compilador genera una creación de instancias.  Cada creación de instancias es una versión de la función con plantilla especializada para el tipo concreto.  Se llamará a esta creación de instancias cada vez que se use la función para el tipo.  Si tiene varias creaciones de instancias idénticas, incluso en módulos diferentes, solo una copia de la creación de instancias terminará agregándose al archivo ejecutable.  
  
 La conversión de argumentos de función se permite en las plantillas de función de cualquier par de argumento y parámetro en el que el parámetro no dependa de un argumento de plantilla.  
  
 Se pueden crear explícitamente instancias de las plantillas de función si la plantilla se declara con un tipo concreto como argumento.  Por ejemplo, se permite el código siguiente:  
  
```  
// function_template_instantiation.cpp  
template<class T> void f(T) { }  
  
// Instantiate f with the explicitly specified template.  
// argument 'int'  
//  
template void f<int> (int);  
  
// Instantiate f with the deduced template argument 'char'.  
template void f(char);  
int main()  
{  
}  
```  
  
## Vea también  
 [Plantillas de función](../cpp/function-templates.md)