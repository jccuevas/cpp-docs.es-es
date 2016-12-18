---
title: "Sobrecargar el operador &gt;&gt; para las clases propias | Microsoft Docs"
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
  - "operador >>, sobrecargar para las clases propias"
  - "operator>>"
  - "operator>>, sobrecargar para las clases propias"
ms.assetid: 40dab4e0-3f97-4745-9cc8-b86e740fa246
caps.latest.revision: 8
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Sobrecargar el operador &gt;&gt; para las clases propias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los flujos de entrada usan el operador de extracción \(`>>`\) para los tipos estándar.  Puede escribir los operadores similares de extracción dispone de tipos; el éxito depende de utilizar el espacio en blanco exacto.  
  
 A continuación se muestra un ejemplo de un operador de extracción para la clase de `Date` mostrada anterior:  
  
```  
istream& operator>> ( istream& is, Date& dt )  
{  
   is >> dt.mo >> dt.da >> dt.yr;  
   return is;  
}  
```  
  
## Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)