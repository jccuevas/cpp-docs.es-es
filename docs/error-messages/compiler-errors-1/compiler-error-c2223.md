---
title: "Error del compilador C2223 | Microsoft Docs"
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
  - "C2223"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2223"
ms.assetid: e4506f0f-0317-4a96-8a90-877a156d7939
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2223
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

izquierda de “\-\>el identificador” debe señalar a struct\/union  
  
 El operando situado a la izquierda de `->` no es un puntero a una clase, estructura o unión.  
  
 Este error puede deberse a que un operando izquierdo es una variable indefinida \(por consiguiente, de tipo `int`\).