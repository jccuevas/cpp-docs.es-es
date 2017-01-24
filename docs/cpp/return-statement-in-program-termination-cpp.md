---
title: "return (Instrucci&#243;n de finalizaci&#243;n del programa) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de datos [C++], tipos de valores devueltos de las funciones"
  - "tipos de valores devueltos de las funciones, return (instrucción)"
  - "return (palabra clave) [C++], sintaxis"
ms.assetid: 66d002ab-5625-4b68-8446-71e1b8fcdbd8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# return (Instrucci&#243;n de finalizaci&#243;n del programa) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Emitir una instrucción `return` desde **main** es equivalente a llamar a la función **exit**.  Considere el ejemplo siguiente:  
  
```  
// return_statement.cpp  
#include <stdlib.h>  
int main()  
{  
    exit( 3 );  
    return 3;  
}  
```  
  
 Las instrucciones **exit** y `return` del ejemplo anterior son funcionalmente idénticas.  Sin embargo, C\+\+ requiere que las funciones que tienen tipos de valor devuelto distintos de `void` devuelvan un valor.  La instrucción `return` permite devolver un valor desde **main**.  
  
## Vea también  
 [Finalización del programa](../cpp/program-termination.md)