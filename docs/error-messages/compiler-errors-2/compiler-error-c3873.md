---
title: "Error del compilador C3873 | Microsoft Docs"
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
  - "C3873"
helpviewer_keywords: 
  - "C3873"
ms.assetid: e68fd3be-2391-492b-ac3f-d2428901b2e9
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3873
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'char': este carácter no se permite como primer carácter de un identificador  
  
 El compilador de C\+\+ respeta el estándar de C\+\+11 respecto de los caracteres permitidos en un identificador. Solo se permiten determinados rangos de caracteres y nombres de carácter universal en un identificador. Se aplican restricciones adicionales respecto del carácter inicial de un identificador. Para obtener más información y una lista de caracteres permitidos y rangos de nombre de carácter universal, consulte [Identificadores de C\+\+](../../cpp/identifiers-cpp.md).  
  
 El rango de caracteres permitidos en un identificador es menos restrictivo cuando se compila código C\+\+\/CLI. Los identificadores del código compilado con \/clr deben regirse por el [Estándar ECMA\-335: Common Language Infrastructure \(CLI\)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).  
  
 En el siguiente ejemplo se genera el error C3873:  
  
```  
// C3873.cpp int main() { int \u036F_abc;   // C3873, not in allowed range for initial character int abc_\u036F;   // OK, in allowed range for non-initial character }  
```