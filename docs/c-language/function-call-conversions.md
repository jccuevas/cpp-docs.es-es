---
title: "Conversiones de llamada de funci&#243;n | Microsoft Docs"
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
helpviewer_keywords: 
  - "llamadas a funciones, conversiones de tipo de argumento"
  - "llamadas a funciones, convertir"
  - "funciones [C], conversiones de argumento"
ms.assetid: 04ea0f81-509a-4913-8b12-0937a81babcf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Conversiones de llamada de funci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El tipo de conversión que se realiza en los argumentos de una llamada a función depende de la presencia de un prototipo de función \(declaración adelantada\) con tipos de argumento declarados para la función llamada.  
  
 Si un prototipo de función está presente e incluye tipos de argumento declarados, el compilador realiza la comprobación de tipos \(vea [Funciones](../c-language/functions-c.md)\).  
  
 Si no hay ningún prototipo de función, solo se realizan las conversiones aritméticas habituales en los argumentos de la llamada a función.  Estas conversiones se realizan independientemente en cada argumento de la llamada.  Esto significa que un valor **float** se convierte en **double**, un valor `char` o **short** se convierte en `int`, y `unsigned char` o **unsigned short** se convierte en `unsigned int`.  
  
## Vea también  
 [Conversiones de tipos](../c-language/type-conversions-c.md)