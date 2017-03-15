---
title: "Error del compilador C2414 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2414"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2414"
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2414
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

número de operandos no válido  
  
### Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado.  Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con un número diferente de operandos.  Ajuste la opción [\/arch \(Arquitectura de CPU mínima\)](../../build/reference/arch-minimum-cpu-architecture.md) para utilizar el procesador más reciente.