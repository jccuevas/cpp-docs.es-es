---
title: "Instrucciones de iteraci&#243;n (C++) | Microsoft Docs"
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
  - "instrucciones de iteración"
  - "estructuras de bucle, instrucciones de iteración"
ms.assetid: bf6d75f7-ead2-426a-9c47-33847f59b8c7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Instrucciones de iteraci&#243;n (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones de iteración producen instrucciones \(o instrucciones compuestas\) que se ejecutarán cero o más veces, según determinados criterios de la finalización de bucle.  Cuando estas instrucciones son instrucciones compuestas, se ejecutan en orden, excepto cuando se encuentra la instrucción [break](../cpp/break-statement-cpp.md) o la instrucción [continue](../cpp/continue-statement-cpp.md).  
  
 C\+\+ proporciona cuatro instrucciones de iteración: [while](../cpp/while-statement-cpp.md), [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md), y [for basado en intervalo](../cpp/range-based-for-statement-cpp.md).  Cada una de ellas se repite hasta que la expresión de finalización se evalúa como cero \(false\) o hasta que se fuerza la finalización del bucle con una instrucción **break**.  En la tabla siguiente se resumen estas instrucciones y sus acciones; cada una se explica detalladamente en las secciones siguientes.  
  
### Instrucciones de iteración  
  
|Instrucción|Se evalúa en|Inicialización|Incremento|  
|-----------------|------------------|--------------------|----------------|  
|`while`|Principio del bucle|No|No|  
|**do**|Final del bucle|No|No|  
|**for**|Principio del bucle|Sí|Sí|  
|**for basado en intervalo**|Principio del bucle|Sí|Sí|  
  
 La parte de instrucción de una instrucción de iteración no puede ser una declaración.  Sin embargo, puede ser una instrucción compuesta que contenga una declaración.  
  
## Vea también  
 [Información general sobre las instrucciones de C\+\+](../cpp/overview-of-cpp-statements.md)