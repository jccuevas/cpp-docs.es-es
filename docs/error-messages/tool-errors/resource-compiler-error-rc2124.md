---
title: "Error del compilador de recursos RC2124 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC2124"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2124"
ms.assetid: 4eb5c4ec-ca9b-46a0-805b-35e040e9ed41
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador de recursos RC2124
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se permiten menús vacíos  
  
 Una palabra clave **END** aparece antes de definir cualquier elemento de menú en la instrucción **MENU**.  El compilador de recursos no permite menús vacíos.  Asegúrese de que no haya ningún signo de comillas abierto dentro de la instrucción **MENU**.