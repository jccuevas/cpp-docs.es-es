---
title: "Advertencia del compilador (nivel 1) C4377 | Microsoft Docs"
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
  - "C4377"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4377"
ms.assetid: a1c797b8-cd5e-4a56-b430-d07932e811cf
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4377
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

de forma predeterminada, los tipos nativos son privados; \- d1PrivateNativeTypes está obsoleto  
  
 En versiones anteriores, los tipos nativos en ensamblados eran públicos de manera predeterminada y se utilizó una opción del compilador interna e indocumentada \(**\/d1PrivateNativeTypes**\), para hacerlos privados.  
  
 Todos los tipos, nativos y CLR, son ahora privados de manera predeterminada en un ensamblado, por lo que ya no necesitan **\/d1PrivateNativeTypes**.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4377.  
  
```  
// C4377.cpp  
// compile with: /clr /d1PrivateNativeTypes /W1  
// C4377 warning expected  
int main() {}  
```