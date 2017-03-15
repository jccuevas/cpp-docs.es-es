---
title: "Advertencia de las herramientas del vinculador LNK4078 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4078"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4078"
ms.assetid: 5a16796d-6caf-42d9-8f65-b042843eafb8
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Advertencia de las herramientas del vinculador LNK4078
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se encontraron varias secciones 'nombre de sección' con atributos diferentes  
  
 LINK encontró dos o más secciones con igual nombre pero diferentes atributos.  
  
 Esta advertencia puede haberla producido una biblioteca de importación o un archivo de exportaciones creado por una versión anterior de LINK o LIB.  
  
 Vuelva a crear el archivo y vincule de nuevo.  
  
## Ejemplo  
 La advertencia LNK4078 también puede haberla causado un cambio importante: la sección a la que [init\_seg](../../preprocessor/init-seg.md) asignó un nombre en x86 era de lectura y escritura, mientras que ahora es de sólo lectura.  
  
 El ejemplo siguiente genera el error LNK4078.  
  
```  
// LNK4078.cpp  
// compile with: /W1  
// LNK4078 expected  
#include <stdio.h>  
#pragma warning(disable : 4075)  
typedef void (__cdecl *PF)(void);  
int cxpf = 0;   // number of destructors to call  
PF pfx[200];   // pointers to destructors.  
  
struct A { A() {} };  
  
int myexit (PF pf) { return 0; }  
  
#pragma section(".mine$a", read, write)  
// try the following line instead  
// #pragma section(".mine$a", read)  
__declspec(allocate(".mine$a")) int ii = 1;  
  
#pragma section(".mine$z", read, write)  
// try the following line instead  
// #pragma section(".mine$z", read)  
__declspec(allocate(".mine$z")) int i = 1;  
  
#pragma data_seg()  
#pragma init_seg(".mine$m", myexit)  
A bbbb;   
A cccc;  
int main() {}  
```