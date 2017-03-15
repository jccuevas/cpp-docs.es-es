---
title: "Error del compilador C2708 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2708"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2708"
ms.assetid: d52d3088-1141-42f4-829c-74755a7fcc3a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2708
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : la longitud de parámetros reales en bytes es distinta respecto a la llamada o referencia anteriores  
  
 Una función [\_\_stdcall](../../cpp/stdcall.md) debe ir precedida de un prototipo.  De lo contrario, el compilador interpreta la primera llamada a la función como un prototipo y este error se produce cuando el compilador encuentra una llamada sin su correspondencia.  
  
 Para resolver este error, agregue un prototipo de función.