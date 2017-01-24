---
title: "Error del compilador C2818 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2818"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2818"
ms.assetid: 715fc7c9-0c6d-452b-b7f5-1682cea5e907
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2818
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

aplicación de 'operador \-\>' sobrecargado es recursiva mediante el tipo “tipo”  
  
 Una nueva definición del operador de acceso a miembros de clase contiene una instrucción `return` recursiva.  Para volver a definir el operador `->` recursivo, se debe mover la rutina recursiva a una función separada a la que se llamará desde la función de reemplazo del operador.