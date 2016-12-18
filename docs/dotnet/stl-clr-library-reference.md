---
title: "Referencia de la biblioteca STL/CLR | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cliext (directorio)"
  - "Biblioteca STL/CLR"
  - "STL/CLR, redistribución"
ms.assetid: a9d9ca00-7bf2-48c1-b205-3ae6f8c25f82
caps.latest.revision: 17
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Referencia de la biblioteca STL/CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La Biblioteca de STL\/CLR es un paquete de la Biblioteca de plantillas estándar \(STL\), un subconjunto de la Biblioteca estándar de C\+\+, para su uso con C\+\+ y .NET Framework Common Language Runtime \(CLR\).  Con STL\/CLR, puede utilizar todos los contenedores, iteradores y algoritmos de STL en un entorno administrado.  
  
 Para utilizar STL\/CLR:  
  
-   Los encabezados de inclusión de **cliext** incluyen el subdirectorio en lugar de los equivalentes habituales de Biblioteca estándar de C\+\+.  
  
-   Califique los nombres de biblioteca con `cliext::` en lugar de `std::`.  
  
 STL\/CLR expone los tipos y las interfaces genéricos que utiliza en escenarios entre ensamblados en el ensamblado de .NET **Microsoft.VisualC.STLCLR.dll**.  Esta DLL se incluye en .NET Framework 3.5.  Si redistribuye una aplicación que utilice STL\/CLR, deberá incluir .NET Framework 3.5, así como cualquier otra biblioteca de Visual C\+\+ que el proyecto utilice, en la sección de las dependencias del proyecto de instalación.  
  
## En esta sección  
 [cliext \(Espacio de nombres\)](../dotnet/cliext-namespace.md)  
 Describe el espacio de nombres que contiene todos los tipos de la Biblioteca de STL\/CLR.  
  
 [Contenedores de STL\/CLR](../dotnet/stl-clr-containers.md)  
 Proporciona información general sobre los contenedores que se encuentran en la biblioteca estándar de C\+\+, incluidos los requisitos para los elementos contenedor, los tipos de elementos que se pueden incrustar y los problemas de propiedad.  
  
 [Requisitos de los elementos contenedores de STL\/CLR](../dotnet/requirements-for-stl-clr-container-elements.md)  
 Describe los requisitos mínimos para todos los tipos de referencia insertados en los contenedores STL.  
  
 [Cómo: Convertir una colección .NET en un contenedor STL\/CLR](../dotnet/how-to-convert-from-a-dotnet-collection-to-a-stl-clr-container.md)  
 Describe cómo convertir una colección de .NET en un contenedor de STL\/CLR.  
  
 [Cómo: Convertir un contenedor STL\/CLR en una colección .NET](../dotnet/how-to-convert-from-a-stl-clr-container-to-a-dotnet-collection.md)  
 Describe cómo convertir un contenedor de STL\/CLR en una colección de .NET.  
  
 [Cómo: Exponer un contenedor de STL\/CLR desde un ensamblado](../dotnet/how-to-expose-an-stl-clr-container-from-an-assembly.md)  
 Muestra cómo mostrar los elementos de varios contenedores de STL\/CLR escritos en un ensamblado de c\+\+.  
  
 Además, en esta sección también se describen los siguientes componentes de STL\/CLR:  
  
|||  
|-|-|  
|[adapter](../dotnet/adapter-stl-clr.md)|[algorithm](../dotnet/algorithm-stl-clr.md)|  
|[deque](../dotnet/deque-stl-clr.md)|[for each, in](../dotnet/for-each-in.md)|  
|[functional](../dotnet/functional-stl-clr.md)|[hash\_map](../dotnet/hash-map-stl-clr.md)|  
|[hash\_multimap](../dotnet/hash-multimap-stl-clr.md)|[hash\_multiset](../dotnet/hash-multiset-stl-clr.md)|  
|[hash\_set](../dotnet/hash-set-stl-clr.md)|[list](../dotnet/list-stl-clr.md)|  
|[map](../dotnet/map-stl-clr.md)|[multimap](../dotnet/multimap-stl-clr.md)|  
|[multiset](../dotnet/multiset-stl-clr.md)|[numeric](../dotnet/numeric-stl-clr.md)|  
|[priority\_queue](../dotnet/priority-queue-stl-clr.md)|[queue](../dotnet/queue-stl-clr.md)|  
|[set](../dotnet/set-stl-clr.md)|[pila](../dotnet/stack-stl-clr.md)|  
|[utility](../dotnet/utility-stl-clr.md)|[vector](../dotnet/vector-stl-clr.md)|  
  
## Vea también  
 [Biblioteca estándar de C\+\+](../standard-library/cpp-standard-library-reference.md)