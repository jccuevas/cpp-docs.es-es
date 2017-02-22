---
title: "Requisitos de los elementos contenedores de STL/CLR | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores, STL"
  - "contenedores, STL/CLR"
  - "Biblioteca estándar de C++, contenedores de clase de plantilla"
  - "STL/CLR, contenedores"
ms.assetid: 59ab240c-15bf-4701-a9f9-e7c56e5ab53f
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Requisitos de los elementos contenedores de STL/CLR
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Todos los tipos de referencia que se insertan en los contenedores de STL\/CLR deben tener, como mínimo, los elementos siguientes:  
  
-   Un constructor público de copia.  
  
-   Un operador de asignación público.  
  
-   Destructor público.  
  
 Además, los contenedores asociativos como [establecer](../dotnet/set-stl-clr.md) y [Mapa](../dotnet/map-stl-clr.md) deben tener un operador de comparación público definido, que es `operator<` de forma predeterminada.  Algunas operaciones en los contenedores también podrían requerir un constructor público predeterminado y un operador de equivalencia público que se va a.  
  
 Como tipos de referencia, los tipos de valor y identificadores a los tipos de referencia que deben se insertarán en un contenedor asociativa deben tener un operador de comparación como `operator<` definido.  Los requisitos para un constructor público de copia, un operador de asignación público, el constructor público no existen para los tipos de valor o identificadores a los tipos de referencia.  
  
## Vea también  
 [Biblioteca de plantillas estándar](../misc/standard-template-library.md)