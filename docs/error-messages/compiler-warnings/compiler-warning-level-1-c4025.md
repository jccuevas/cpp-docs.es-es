---
title: "Advertencia del compilador (nivel 1) C4025 | Microsoft Docs"
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
  - "C4025"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4025"
ms.assetid: c4f6a651-0641-4446-973e-8290065e49ad
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4025
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'number': el puntero de tipo basado se pasó a la función con los argumentos de variable: parámetro número  
  
 Si se pasa un puntero de tipo basado a una función con argumentos de variable, el puntero se normaliza, con resultados imprevisibles. No pase punteros de tipo basado a funciones con argumentos de variable.