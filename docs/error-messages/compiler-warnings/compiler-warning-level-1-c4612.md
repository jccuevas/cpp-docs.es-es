---
title: "Advertencia del compilador (nivel 1) C4612 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4612"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4612"
ms.assetid: 21ac02b2-51cd-4aff-9b70-d543511d5962
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4612
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error en el nombre de archivo de inclusión  
  
 Esta advertencia se produce con **\#pragma include\_alias** cuando un nombre de archivo es incorrecto o falta.  
  
 Los argumentos para la instrucción **\#pragma include\_alias** puede usar las comillas \(**"***filename***"**\) o los corchetes angulares \(**\<***filename***\>**\), pero ambos deben usar el mismo formato.  
  
## Ejemplo  
  
```  
// C4612.cpp // compile with: /W1 /LD #pragma include_alias("StandardIO", <stdio.h>) // C4612  
```