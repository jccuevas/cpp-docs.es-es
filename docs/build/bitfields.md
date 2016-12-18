---
title: "Campos de bits | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "campos de bits"
ms.assetid: e9a1010d-1e1b-487f-9943-3c574e08f544
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Campos de bits
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los campos de bits de estructura se limitan a 64 bits y pueden ser de tipo con signo int, int sin signo, int64 o int64 sin signo.  Los campos de bits que cruzan el límite de tipo omitirán bits para alinear el campo con la alineación de tipo siguiente.  Por ejemplo, los campos de bits enteros no pueden cruzar un límite de 32 bits.  
  
## Vea también  
 [Tipos y almacenamiento](../build/types-and-storage.md)