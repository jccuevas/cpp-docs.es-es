---
title: "Advertencia del compilador (nivel 1) C4027 | Microsoft Docs"
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
  - "C4027"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4027"
ms.assetid: f30d57b9-20c4-4284-8686-566d9f0ca7fc
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4027
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

función declarada sin lista de parámetros formales  
  
 La declaración de función no toma parámetros formales, pero existen parámetros formales en la definición de función o parámetros reales en una llamada. Las llamadas posteriores a esta función suponen que la función toma parámetros reales de los tipos encontrados en la definición de función o la llamada.