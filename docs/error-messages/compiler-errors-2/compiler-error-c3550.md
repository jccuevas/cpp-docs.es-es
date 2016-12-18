---
title: "Compiler Error C3550 | Microsoft Docs"
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
  - "C3550"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3550"
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Compiler Error C3550
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

solo se permite 'decltype\(auto\)' sin formato en este contexto  
  
 Si se usa `decltype(auto)` como marcador de posición para el tipo de valor devuelto de una función, debe usarse por sí mismo.  No se puede usar como parte de una declaración de puntero \(`decltype(auto*)`\), una declaración de referencia \(`decltype(auto&)`\) o cualquier otra cualificación similar.  
  
## Vea también  
 [auto](../../cpp/auto-cpp.md)