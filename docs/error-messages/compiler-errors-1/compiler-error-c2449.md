---
title: "Error del compilador C2449 | Microsoft Docs"
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
  - "C2449"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2449"
ms.assetid: 544bf0b6-daa0-40e8-9f21-8e583d472a2d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2449
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se encontró '{' en el ámbito de archivo \(¿falta el encabezado de función?\)  
  
 Hay una llave de apertura en el ámbito de archivo.  
  
 La causa de este error puede ser la presencia de un punto y coma entre un encabezado de función y la llave de apertura de la definición de función.  
  
 El código siguiente genera el error C2499:  
  
```  
// C2449.c  
// compile with: /c  
void __stdcall func(void) {}   // OK  
void __stdcall func(void);  // extra semicolon on this line  
{                         // C2449 detected here  
```