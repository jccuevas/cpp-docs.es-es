---
title: "Convenciones de llamada obsoletas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "__fortran"
  - "__pascal"
  - "__syscall"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__fortran (palabra clave) [C++]"
  - "__pascal (palabra clave) [C++]"
  - "__syscall (palabra clave) [C++]"
  - "convenciones de llamada, obsoletas"
  - "WINAPI"
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Convenciones de llamada obsoletas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Las convenciones de llamada **\_\_pascal**, **\_\_fortran** y **\_\_syscall** ya no se admiten.  Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.  
  
 WINDOWS.H admite ahora la macro de **WINAPI**, que traslada a la convención de llamada adecuada para el destino.  Utilice **WINAPI** donde antes utilizaba **PASCAL** o **\_\_far \_\_pascal**.  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)