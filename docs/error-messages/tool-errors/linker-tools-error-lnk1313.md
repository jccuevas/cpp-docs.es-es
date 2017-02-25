---
title: "Error de las herramientas del vinculador LNK1313 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1313"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1313"
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1313
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

módulo ijw\/native detectado; no se puede vincular con módulos puros  
  
 La versión actual de Visual C\+\+ no admite la vinculación de archivos .obj administrados\/nativos en modo nativo o mixto con archivos .obj compilados con **\/clr:pure**.  
  
## Ejemplo  
  
```  
// LNK1313.cpp  
// compile with: /c /clr:pure  
// a pure module  
int main() {}  
```  
  
## Ejemplo  
  
```  
// LNK1313_b.cpp  
// compile with: /c /clr  
// an IJW module  
void test(){}  
```  
  
## Ejemplo  
 El ejemplo siguiente generará el error LNK1313.  
  
```  
// LNK1313_c.cpp  
// compile with: /link LNK1313.obj LNK1313_b.obj  
// LNK1313 warning expected  
```