---
title: "Variables autom&#225;ticas (&#225;mbito de funci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "variables automáticas"
  - "funciones [C++], ámbito"
  - "ámbito, declarado en funciones"
  - "variables, automáticamente"
ms.assetid: 6e1a14c2-1fb0-4937-8628-8d963cc35ed4
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Variables autom&#225;ticas (&#225;mbito de funci&#243;n)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una variable declarada dentro de una función sólo puede utilizarse en el ámbito de dicha función.  
  
```  
// LNK2019_AV.cpp  
// compile with: /c  
void test(void);  
  
static int lnktest3 = 3;  
int lnktest4 = 4;  
  
int main() {  
   static int lnktest1 = 1;  
   int lnktest2 = 2;  
   test();  
}  
```  
  
 y, a continuación,  
  
```  
// LNK2019_AV_2.cpp  
// compile with: LNK2019_AV.cpp  
// LNK2019 expected  
extern int lnktest1;  
extern int lnktest2;  
extern int lnktest3;  
extern int lnktest4;  
  
void test(void) {  
   int i = 0;  
   i = lnktest1;  
   i = lnktest2;  
   i = lnktest3;  
   i = lnktest4;   // OK  
}  
```  
  
## Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)