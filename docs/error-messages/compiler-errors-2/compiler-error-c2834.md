---
title: "Error del compilador C2834 | Microsoft Docs"
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
  - "C2834"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2834"
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2834
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operator operador' se debe calificar globalmente  
  
 Los operadores `new` y `delete` están asociados a la clase donde residen.  No se puede utilizar la resolución de ámbito para seleccionar una versión de `new` o `delete` de una clase diferente.  Para implementar varias formas del operador `new` o `delete`, cree una versión del operador con parámetros formales adicionales.