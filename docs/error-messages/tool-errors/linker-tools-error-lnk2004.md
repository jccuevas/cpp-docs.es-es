---
title: "Error de las herramientas del vinculador LNK2004 | Microsoft Docs"
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
  - "LNK2004"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2004"
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK2004
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento de corrección relativo de gp en 'destino'; la sección corta 'sección' es demasiado grande o está fuera de intervalo  
  
 La sección es demasiado grande.  
  
 Para resolver este error, reduzca el tamaño de la sección corta colocando datos explícitamente en las secciones largas mediante la directiva pragma \#pragma section\(".sectionname", read, write, long\) y utilizando `__declspec(allocate(".sectionname"))` en las definiciones y en las declaraciones de datos.  Por ejemplo,  
  
```  
#pragma section(".data$mylong", read, write, long)  
__declspec(allocate(".data$mylong"))  
char    rg0[1] = { 1 };  
char    rg1[2] = { 1 };  
char    rg2[4] = { 1 };  
char    rg3[8] = { 1 };  
char    rg4[16] = { 1 };  
char    rg5[32] = { 1 };  
```  
  
 También puede mover datos agrupados mediante criterios lógicos a una estructura propia, que será una recolección de datos de un tamaño mayor de 8 bytes que el compilador asignará a una sección de datos de tipo long.  Por ejemplo,  
  
```  
// from this...  
int     w1  = 23;  
int     w2 = 46;  
int     w3 = 23*3;  
int     w4 = 23*4;  
  
// to this...  
struct X {  
    int     w1;  
    int     w2;  
    int     w3;  
    int     w4;  
} x  = { 23, 23*2, 23*3, 23*4 };  
  
```  
  
 Este error va seguido del error irrecuperable `LNK1165`.