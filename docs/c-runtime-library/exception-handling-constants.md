---
title: "Constantes para el control de excepciones | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EXCEPTION_CONTINUE_SEARCH"
  - "c.constants"
  - "EXCEPTION_CONTINUE_EXECUTION"
  - "EXCEPTION_EXECUTE_HANDLER"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "EH (constantes)"
  - "control de excepciones, constantes"
  - "EXCEPTION_CONTINUE_EXECUTION (constante)"
  - "EXCEPTION_CONTINUE_SEARCH (constante)"
  - "EXCEPTION_EXECUTE_HANDLER (constante)"
ms.assetid: e1870f41-be9e-46a3-a2ea-830dfbaa18fb
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes para el control de excepciones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se devuelve `EXCEPTION_CONTINUE_SEARCH`constante, `EXCEPTION_CONTINUE_EXECUTION`, o `EXCEPTION_EXECUTE_HANDLER` cuando se produce una excepción durante la ejecución de la sección guardada de una instrucción de **try\-except** .  El valor devuelto determina cómo se controla la excepción.  Para obtener más información, vea [intento\-excepto la instrucción](../cpp/try-except-statement.md) en *la referencia del lenguaje C\+\+*.  
  
## Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)