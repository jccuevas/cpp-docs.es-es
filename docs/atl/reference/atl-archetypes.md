---
title: "ATL Archetypes | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "archetype"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL, archetypes"
ms.assetid: 809fb0af-c0f4-4cc0-b5bc-afe3de5d9722
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL Archetypes
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En este contexto, *un arquetipo* es una clase teórica que proporciona una colección de métodos, miembros de datos, funciones estáticas, de typedefs, u otras características.  el arquetipo también incluye una descripción de la semántica necesaria crear o utilizar la clase para representar un concepto determinado.  Las clases que imitan el arquetipo proporcionando las mismas características personifican el mismo concepto y pueden utilizarse en cualquier parte que el arquetipo pueden utilizar.  
  
 Los arquetipos son útiles en C\+\+ para describir las características de los valores válidos para los parámetros de plantilla.  El diseñador de plantilla tiene una idea clara de las características necesarias y suficientes de parámetros de plantilla, y el compilador aplicará los requisitos de sintaxis en tiempo de compilación, pero el usuario de una plantilla necesita la documentación describir la semántica y permitir las relaciones entre los arquetipos y clases que se explicarán claramente.  
  
 Los ejemplos de arquetipos en la biblioteca estándar de C\+\+ son los diferentes tipos de iterador y de contenedor.  estos arquetipos se describen en los temas [Convenciones de iterador](../../standard-library/iterators.md) y [Contenedores STL](../../standard-library/stl-containers.md).  
  
 el servidor ATL define los arquetipos siguientes:  
  
|Name|Descripción|  
|----------|-----------------|  
|[Arquetipo worker](../../atl/reference/worker-archetype.md)|Las clases que se ajustan al arquetipo *worker* proporcionan el código a los elementos de trabajo de proceso en cola en un grupo de subprocesos.|  
  
## Vea también  
 [Conceptos](../../atl/active-template-library-atl-concepts.md)   
 [ATL COM Desktop Components](../../atl/atl-com-desktop-components.md)