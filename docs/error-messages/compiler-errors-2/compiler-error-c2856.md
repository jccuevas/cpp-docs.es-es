---
title: "Error del compilador C2856 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2856"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2856"
ms.assetid: fe616c51-124e-49e3-9dd8-883ec1660680
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2856
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\#pragma hdrstop no puede estar dentro de un bloque \#if  
  
 La pragma `hdrstop` no se puede insertar en el cuerpo de un bloque de compilación condicional.  
  
 Mueva la instrucción `#pragma hdrstop` a un área que no esté contenida en un bloque `#if/#endif`.