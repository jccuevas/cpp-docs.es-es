---
title: "Cambios generales en el lenguaje (C++/CLI) | Microsoft Docs"
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
ms.assetid: 79a70768-225c-4ae2-84d1-178b20a9b042
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cambios generales en el lenguaje (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Varias características del lenguaje de CLR han cambiado de Extensiones administradas para C\+\+ a [!INCLUDE[cpp_current_long](../dotnet/includes/cpp_current_long_md.md)].  
  
 Los cambios descritos en esta sección son una especie de miscelánea del lenguaje.  Incluye un cambio en el control de literales de cadena, un cambio en la resolución de sobrecarga entre los puntos suspensivos y el atributo `Param`, el cambio de `typeof` a `typeid`, un cambio en la llamada de las listas de inicializadores del constructor y la introducción de una nueva notación de conversión de tipos, `safe_cast`.  
  
 [Literal de cadena](../dotnet/string-literal.md)  
 Explica cómo ha cambiado el control de literales de cadena.  
  
 [Matriz de parámetros y puntos suspensivos](../dotnet/param-array-and-ellipsis.md)  
 Explica cómo `ParamArray` ahora tiene prioridad sobre los puntos suspensivos \(`…`\) para resolver llamadas a funciones que tienen un número de argumentos variable.  
  
 [T::typeid reemplaza typeof](../dotnet/typeof-goes-to-t-typeid.md)  
 Explica cómo `typeid` ha suplantado al operador `typeof`.  
  
 [Listas de inicializadores](../dotnet/initializer-lists.md)  
 Describe los cambios realizados en el orden de llamada de las listas de inicializadores.  
  
 [Notación de conversión e introducción de safe\_cast\<\>](../dotnet/cast-notation-and-introduction-of-safe-cast-angles.md)  
 Trata sobre los cambios de la notación de conversión de tipos y en particular de la introducción de `safe_cast`.  
  
## Vea también  
 [Manual de migraciones C\+\+\/CLI](../dotnet/cpp-cli-migration-primer.md)