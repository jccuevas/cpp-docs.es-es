---
title: "Advertencia del compilador (nivel 3) C4278 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4278"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4278"
ms.assetid: 4b6053fb-df62-4c04-b6c8-c011759557b8
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 3) C4278
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador': el identificador de la biblioteca de tipos 'tlb' ya es una macro; utilice el calificador 'rename'  
  
 Al utilizar [\#import](../../preprocessor/hash-import-directive-cpp.md), un identificador de la biblioteca de tipos que se está importando intenta declarar un identificador ***identifier***.  Sin embargo, éste ya constituye un símbolo válido.  
  
 Utilice el atributo `#import` **rename** para asignar un alias al símbolo de la biblioteca de tipos.