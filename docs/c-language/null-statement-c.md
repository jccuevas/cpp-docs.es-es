---
title: "NULL (Instrucci&#243;n) (C) | Microsoft Docs"
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
  - "expresiones [C++], null"
  - "null (instrucción)"
  - "valores nulos, expresiones"
  - "punto y coma, null en C (instrucción)"
ms.assetid: 72576ce6-26d0-4379-be65-fee522088790
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# NULL (Instrucci&#243;n) (C)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una "instrucción null" es una instrucción que solo contiene un punto y coma; puede aparecer en cualquier lugar donde se espere una instrucción.  No ocurre nada cuando se ejecuta una instrucción null.  La manera correcta de escribir una instrucción null es:  
  
## Sintaxis  
  
```  
  
;  
  
```  
  
## Comentarios  
 Las instrucciones como **do**, **for**, **if** y `while` requieren que aparezca una instrucción ejecutable como cuerpo de la instrucción.  La instrucción null cumple el requisito sintáctico en los casos en que no se necesita un cuerpo de instrucción sustancial.  
  
 Como con cualquier otra instrucción de C, puede incluir una etiqueta delante de una instrucción null.  Para etiquetar un elemento que no es una instrucción, como la llave de cierre de una instrucción compuesta, puede etiquetar una instrucción null e insertarla inmediatamente delante del elemento para obtener el mismo efecto.  
  
 En este ejemplo se ilustra la instrucción null:  
  
```  
for ( i = 0; i < 10; line[i++] = 0 )  
     ;  
```  
  
 En este ejemplo, la expresión de bucle de la instrucción **for** `line[i++] = 0` inicializa los 10 primeros elementos de `line` en 0.  El cuerpo de la instrucción es una instrucción null, ya que no se requieren más instrucciones.  
  
## Vea también  
 [Instrucciones](../c-language/statements-c.md)