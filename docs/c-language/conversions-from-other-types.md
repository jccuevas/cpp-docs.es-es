---
title: "Conversiones desde otros tipos | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "conversiones de tipos, conversión"
  - "valores, convertir"
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conversiones desde otros tipos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puesto que un valor `enum` es un valor `int` por definición, las conversiones de y a valores `enum` son iguales que las del tipo `int`.  Para el compilador de Microsoft C, un entero es igual que **long**.  
  
 **Específicos de Microsoft**  
  
 No se permite ninguna conversión entre tipos de estructura o unión.  
  
 Cualquier valor se puede convertir al tipo `void`, pero el resultado de dicha conversión solo se puede utilizar en un contexto donde se descarte un valor de expresión, como una instrucción de expresión.  
  
 El tipo `void` no tiene ningún valor, por definición.  Por consiguiente, no se puede convertir en ningún otro tipo, y otros tipos no pueden convertirse en `void` por asignación.  Sin embargo, se puede convertir explícitamente un valor al tipo `void`, como se describe en [Conversiones de tipos](../c-language/type-cast-conversions.md).  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Conversiones de asignación](../c-language/assignment-conversions.md)