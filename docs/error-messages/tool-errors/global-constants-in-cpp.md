---
title: "Constantes globales en C++ | Microsoft Docs"
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
  - "constantes, globales"
  - "constantes globales"
ms.assetid: df5a9bd4-d0a8-4c1c-956e-b481d0bded7d
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Constantes globales en C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las constantes globales de C\+\+ tienen vinculación externa.  Esto es diferente en C.  Si se intenta utilizar una constante global en C\+\+ en varios archivos, se obtiene un error externo no resuelto.  El compilador optimiza las constantes globales, sin dejar espacio reservado para la variable.  
  
 Un modo de solucionarlo consiste en incluir las inicializaciones de constante en un archivo de encabezado e incluir dicho encabezado en los archivos CPP cuando sea necesario, como si fuera un prototipo de función.  Otra posibilidad es hacer no constante la variable y utilizar una referencia de constante al evaluarla.  
  
 El código siguiente genera el error C2019:  
  
```  
// global_constants.cpp  
// LNK2019 expected  
void test(void);  
const int lnktest1 = 0;  
  
int main() {  
   test();  
}  
```  
  
 Y, a continuación,  
  
```  
// global_constants_2.cpp  
// compile with: global_constants.cpp  
extern int lnktest1;  
  
void test() {  
  int i = lnktest1;   // LNK2019  
}  
```  
  
## Vea también  
 [Error de las herramientas del vinculador LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md)