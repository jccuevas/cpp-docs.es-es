---
title: "Error de BSCMAKE BK1509 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1509"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1509"
ms.assetid: 53df7037-1913-4b63-b425-c0bf44081792
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de BSCMAKE BK1509
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sin espacio en el montón  
  
 BSCMAKE necesita más memoria, incluyendo memoria virtual.  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Libere espacio en disco.  
  
2.  Aumente el tamaño del archivo de intercambio.  
  
3.  Aumente el tamaño del archivo de intercambio de Windows.  
  
4.  Reduzca la memoria que requiere BSCMAKE mediante \/Ei o \/Es para eliminar algunos archivos de entrada o \/Em para eliminar cuerpos de macro.