---
title: "Advertencia del compilador (nivel 1) C4506 | Microsoft Docs"
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
  - "C4506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4506"
ms.assetid: aa682869-65d1-4dad-ba32-198f10b44f91
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no hay una definición para la función inline 'función'  
  
 La función dada se declaró y marcó para su ejecución en línea, pero no se definió.  
  
 El compilador no procesó la función en línea.  
  
 Asegúrese de que las funciones externas que haya que procesar en línea se declaren con la palabra clave `extern`.