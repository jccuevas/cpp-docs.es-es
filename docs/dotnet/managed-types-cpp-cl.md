---
title: "Tipos administrados (C++/CL) | Microsoft Docs"
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
  - "__gc (tipos)"
  - "tipos [C++], CLR"
ms.assetid: 1ddd114e-be02-4de7-a4dd-a2d72ad8ff81
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos administrados (C++/CL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sintaxis para la declaración de tipos administrados, y la creación y el uso de objetos de estos tipos se ha alterado significativamente de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  Esto se ha hecho para promover su integración dentro del sistema de tipos de ISO\-C\+\+.  Estos cambios se presentan en detalle en las subsecciones siguientes.  
  
## En esta sección  
 [Declaración de un tipo de clase administrada](../dotnet/declaration-of-a-managed-class-type.md)  
 Describe cómo declarar una `class`, `struct` o `interface` administrados.  
  
 [Declaración de un objeto de una clase de referencia de CLR](../dotnet/declaration-of-a-clr-reference-class-object.md)  
 Describe cómo declarar un objeto de tipo de clase de referencia mediante un controlador de seguimiento.  
  
 [Declaración de una matriz de CLR](../dotnet/declaration-of-a-clr-array.md)  
 Explica cómo declarar e inicializar una matriz.  
  
 [Cambios en el orden de inicialización de constructores](../dotnet/changes-in-constructor-initialization-order.md)  
 Analiza los cambios clave en el orden de inicialización de los constructores de clase.  
  
 [Cambios en la semántica de los destructores](../dotnet/changes-in-destructor-semantics.md)  
 Describe la finalización no determinista, `Finalize` frente a `Dispose`, las ramificaciones para los objetos de referencia y el uso de `Finalize` explícito.  
  
 **Nota:** la descripción de delegados se aplaza hasta que [Delegados y eventos](../dotnet/delegates-and-events.md) para presentarlos con miembros de eventos dentro de una clase, el tema general de [Declaraciones de miembros en una clase o interfaz \(C\+\+\/CLI\)](../dotnet/member-declarations-within-a-class-or-interface-cpp-cli.md).  
  
## Vea también  
 [Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md)   
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)   
 [Matrices](../windows/arrays-cpp-component-extensions.md)