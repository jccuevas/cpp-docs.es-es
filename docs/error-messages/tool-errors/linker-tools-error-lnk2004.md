---
title: Las herramientas del vinculador LNK2004 Error | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK2004
dev_langs: C++
helpviewer_keywords: LNK2004
ms.assetid: 07645371-e67b-4a2c-b0e0-dde24c94ef7e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3fdbd32bbc59d9c18df5544f07ec7e7097b9e02e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2004"></a>Error de las herramientas del vinculador LNK2004
desbordamiento de corrección relativo de GP en 'destino'; breve sección 'sección' es demasiado grande o fuera del intervalo.  
  
 La sección era demasiado grande.  
  
 Para resolver este error, reduzca el tamaño de la sección corto, ya sea explícitamente colocar datos en las secciones largas mediante #pragma section (".sectionname", lectura, escritura, long) y utilizando `__declspec(allocate(".sectionname"))` en declaraciones y definiciones de datos.  Por ejemplo,  
  
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
  
 También puede mover datos agrupados lógicamente en su propia estructura, que es una colección de datos mayores de 8 bytes, que el compilador asignará en una sección de datos de tipo long.  Por ejemplo,  
  
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
  
 Este error se sigue por error irrecuperable `LNK1165`.