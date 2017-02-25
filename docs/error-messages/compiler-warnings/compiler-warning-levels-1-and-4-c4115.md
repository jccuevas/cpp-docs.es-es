---
title: "Advertencia del compilador (niveles 1 y 4) C4115 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4115"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4115"
ms.assetid: f3f94e72-fc49-4d09-b3e7-23d68e61152f
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Advertencia del compilador (niveles 1 y 4) C4115
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type': definición de tipo con nombre entre paréntesis  
  
 Un símbolo determinado se usa para definir una estructura, una unión o un tipo enumerado dentro de una expresión entre paréntesis. El ámbito de la definición de puede ser inesperado.  
  
 En una llamada de función de C, la definición tiene ámbito global. En una llamada de C\+\+, la definición tiene el mismo ámbito que la función que se llama.  
  
 Esta advertencia puede deberse también a declaradores entre paréntesis \(como los prototipos\) que no son expresiones entre paréntesis.  
  
 Se trata de una advertencia de nivel 1 con programas de C\+\+ y programas de C que se compilaron con la compatibilidad con ANSI \(\/Za\). De lo contrario, es de nivel 3.