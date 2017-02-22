---
title: "Subdesbordamiento de valores de punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 78af8016-643c-47db-b4f1-7f06cb4b243e
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Subdesbordamiento de valores de punto flotante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 4.5.1** Si las funciones matemáticas establecen la expresión de entero `errno` en el valor de la macro `ERANGE` en errores de intervalo de subdesbordamiento  
  
 Un subdesbordamiento de punto flotante no establece la expresión `errno` en `ERANGE`.  Cuando un valor se aproxima a cero y finalmente sufre subdesbordamiento, el valor se establece en cero.  
  
## Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)