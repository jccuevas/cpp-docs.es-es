---
title: "Matrices en expresiones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "matrices [C++], en expresiones"
  - "expresiones [C++], matrices en"
ms.assetid: 6e5a795b-d6bd-4e39-b313-6a20d47c4d4b
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Matrices en expresiones
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un identificador de un tipo de matriz aparece en una expresión distinta de `sizeof`, dirección de \(**&**\) o inicialización de una referencia, se convierte en un puntero al primer elemento de matriz.  Por ejemplo:  
  
```  
char szError1[] = "Error: Disk drive not ready.";  
char *psz = szError1;  
```  
  
 El puntero `psz` apunta al primer elemento de la matriz `szError1`.  Tenga en cuenta que las matrices, a diferencia de los punteros, no son valores l modificables.  Por consiguiente, la siguiente asignación no es válida:  
  
```  
szError1 = psz;  
```  
  
## Vea también  
 [Matrices](../cpp/arrays-cpp.md)