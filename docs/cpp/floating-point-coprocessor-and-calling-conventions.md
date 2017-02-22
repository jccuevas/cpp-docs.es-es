---
title: "Coprocesador de punto flotante y convenciones de llamada | Microsoft Docs"
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
  - "coprocesador de punto flotante"
  - "números de punto flotante"
  - "números de punto flotante, coprocesador"
ms.assetid: 3cc6615a-b308-4cf7-9570-83e192a832b3
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Coprocesador de punto flotante y convenciones de llamada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si va a escribir rutinas de ensamblado para el coprocesador de punto flotante, debe conservar la palabra de control de punto flotante y limpiar la pila del coprocesador a menos que vaya a devolver un valor **float** o **double** \(que debería devolver la función en ST\(0\)\).  
  
## Vea también  
 [Convenciones de llamada](../cpp/calling-conventions.md)