---
title: "Error del compilador C3661 | Microsoft Docs"
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
  - "C3661"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3661"
ms.assetid: 50793fd1-1829-4b29-ad0d-094ef2068b43
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3661
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la lista de reemplazo explícita no encontró ningún método para reemplazar  
  
 Un reemplazo explícito especificaba uno o varios nombres de tipo.  Sin embargo, no había ninguna función con la firma necesaria en los tipos que coincidiera con la firma de la función de reemplazo.  Si intenta reemplazar basándose en el nombre de tipo, habrá una o varias funciones virtuales en los tipos especificados que coincidan con la firma de la función de reemplazo.  
  
 Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).