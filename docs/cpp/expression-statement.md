---
title: "Expression (Instrucci&#243;n) | Microsoft Docs"
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
  - "instrucciones de expresión"
  - "instrucciones, expresión"
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Expression (Instrucci&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las instrucciones de expresión hacen que se evalúen las expresiones.  No se realiza ninguna transferencia de control o iteración como resultado de una instrucción de expresión.  
  
 La sintaxis de la instrucción de expresión es simplemente  
  
## Sintaxis  
  
```  
[expression ] ;  
```  
  
## Comentarios  
 Todas las expresiones de una instrucción de expresión se evalúan y se aplican todos los efectos secundarios antes de que se ejecute la siguiente instrucción.  Las instrucciones de expresión más comunes son las asignaciones y las llamadas a funciones.  Puesto que la expresión es opcional, un punto y coma solo se considera una instrucción de expresión vacía, denominada instrucción [null](../cpp/null-statement.md).  
  
## Vea también  
 [Información general sobre las instrucciones de C\+\+](../cpp/overview-of-cpp-statements.md)