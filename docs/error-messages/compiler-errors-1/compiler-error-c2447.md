---
title: "Error del compilador C2447 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2447"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2447"
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2447
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'{': falta el encabezado de función \(¿lista formal de estilo anterior?\)  
  
 El compilador encontró una llave de apertura inesperada en el ámbito global.  En la mayoría de los casos, la causa está en un encabezado de función que tiene un formato incorrecto, una declaración mal colocada o carácter de punto y coma desubicado.  Para resolver este problema, compruebe que la llave de apertura va detrás de un encabezado con formato correcto y no va precedida de una declaración o un carácter de punto y coma desubicado.  
  
 Este error también puede deberse a una lista de argumentos formales del lenguaje C de estilo anterior.  Para resolver este problema, refactorice la lista de argumentos para que utilice un estilo moderno; es decir, que vaya entre paréntesis.  
  
 En el ejemplo siguiente se genera el error C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```