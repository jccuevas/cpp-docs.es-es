---
title: "Convertir valores enteros en valores de punto flotante | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "enteros, convertir a valores de punto flotante"
ms.assetid: 81fd5b7d-15eb-4c11-a8c8-e1621ff54fd3
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Convertir valores enteros en valores de punto flotante
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**ANSI 3.2.1.3** La dirección de truncamiento cuando un número entero se convierte en un número de punto flotante que no puede representar exactamente el valor original  
  
 Cuando un número entero se convierte en un valor de punto flotante que no puede representar exactamente el valor, el valor se redondea \(arriba o abajo\) al valor apropiado más próximo.  
  
 Por ejemplo, la conversión de **unsigned long** \(con 32 bits de precisión\) a **float** \(cuya mantisa tiene 23 bits de precisión\) redondea el número al múltiplo más próximo de 256.  Los valores **long** 4.294.966.913 a 4.294.967.167 se redondean todos ellos al valor **float** 4.294.967.040.  
  
## Vea también  
 [Matemáticas de punto flotante](../c-language/floating-point-math.md)