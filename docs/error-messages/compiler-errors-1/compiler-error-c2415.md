---
title: "Error del compilador C2415 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2415"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2415"
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2415
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

tipo de operando incorrecto  
  
 El código de operación no utiliza los operandos de este tipo.  
  
### Posibles causas del error:  
  
1.  El código de operación no admite el número de operandos utilizado.  Revise el manual de referencia del lenguaje de ensamblado para determinar el número correcto de operandos.  
  
2.  Un procesador más reciente admite la instrucción con tipos adicionales.  Ajuste la opción [\/arch \(Arquitectura de CPU mínima\)](../../build/reference/arch-minimum-cpu-architecture.md) para utilizar el procesador más reciente.