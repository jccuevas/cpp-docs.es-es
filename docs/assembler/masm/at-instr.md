---
title: "@InStr | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "@InStr"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "@InStr symbol"
ms.assetid: 980d5b9f-2b88-4306-8955-df6cd2133e68
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# @InStr
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Función de macro que busca la primera aparición *de string2* en *string1*, comenzando en *la posición* *de string1*.  Si no aparece *la posición* , buscar comienza en el inicio *de string1*.  devuelve un entero o un 0 de la posición si *string2* no se encuentra.  
  
## Sintaxis  
  
```  
  
@InStr( [[position]], string1, string2 )  
```  
  
## Vea también  
 [Symbols Reference](../../assembler/masm/symbols-reference.md)