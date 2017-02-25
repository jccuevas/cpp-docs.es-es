---
title: "Informaci&#243;n de tipos en tiempo de ejecuci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RTTI (opción del compilador)"
  - "tiempo de ejecución, comprobación de tipos"
  - "comprobaciones en tiempo de ejecución, comprobación de tipos"
  - "información de tipo en tiempo de ejecución"
  - "información de tipos, comprobación de tipo en tiempo de ejecución"
ms.assetid: becbd0e5-0439-4c61-854f-8a74f7160c54
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Informaci&#243;n de tipos en tiempo de ejecuci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La información de tipo en tiempo de ejecución \(RTTI\) es un mecanismo que permite determinar el tipo de un objeto durante la ejecución del programa.  RTTI se agregó al lenguaje C\+\+ porque muchos proveedores de bibliotecas de clases implementaban esta funcionalidad por sí mismos.  Esto produjo incompatibilidades entre las bibliotecas.  Por tanto, se hizo obvio que se necesitaba compatibilidad para información de tipo en tiempo de ejecución en el nivel de lenguaje.  
  
 Por razones de claridad, esta discusión de RTTI se limita casi totalmente a punteros.  Sin embargo, los conceptos discutidos también se aplican a referencias.  
  
 Hay tres elementos principales del lenguaje C\+\+ para la información en tiempo de ejecución:  
  
-   El operador [dynamic\_cast](../cpp/dynamic-cast-operator.md).  
  
     Se usa para la conversión de tipos polimórficos.  
  
-   El operador [typeid](../cpp/typeid-operator.md).  
  
     Se utiliza para identificar el tipo exacto de un objeto.  
  
-   La clase [type\_information](../cpp/type-info-class.md).  
  
     Se usa para contener la información de tipo devuelta por el operador `typeid`.  
  
## Vea también  
 [Convertir](../cpp/casting.md)