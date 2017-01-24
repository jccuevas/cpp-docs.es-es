---
title: "Los par&#225;metros de &lt;tipo&gt; no se pueden declarar como &#39;Optional&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc33010"
  - "vbc33010"
helpviewer_keywords: 
  - "BC33010"
ms.assetid: ec4023e7-9ba6-4532-a6b9-4ae6b4f9063a
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Los par&#225;metros de &lt;tipo&gt; no se pueden declarar como &#39;Optional&#39;
Una definición de un delegado, evento u operador declara un parámetro [Optional](../Topic/Optional%20\(Visual%20Basic\).md).  
  
 Los parámetros `Optional` solo se permiten en los parámetros `Declare`, `Function`, `Property` y `Sub`.  
  
 **Identificador de error:** BC33010  
  
### Para corregir este error  
  
-   Quite la palabra clave `Optional` de la lista de parámetros.  
  
-   Si va a definir un operador, quizás puede conseguir la función `Optional` con una serie de sobrecargas.  
  
-   Si está definiendo un delegado o un evento, debe rehacer toda la lógica de esta parte de la aplicación. No puede usar los parámetros `Optional` o [ParamArray](../Topic/ParamArray%20\(Visual%20Basic\).md), ni versiones sobrecargadas, en parámetros de delegado o evento.  
  
## Vea también  
 [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md)   
 [Procedimientos de operador](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator \(Instrucción\)](../Topic/Operator%20Statement.md)