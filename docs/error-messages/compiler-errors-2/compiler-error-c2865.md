---
title: "Error del compilador C2865 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2865"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2865"
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2865
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : comparación no válida para handle\_or\_pointer  
  
 Se pueden comparar referencias a [Clases y structs](../../windows/classes-and-structs-cpp-component-extensions.md) o tipos [\_\_gc](../../misc/gc.md) sólo a efectos de igualdad, para comprobar si hacen referencia al mismo objeto \(\=\=\) o a objetos diferentes \(\!\=\).  
  
 No se pueden comparar para ordenarlas, ya que el motor en tiempo de ejecución .NET podría mover los objetos administrados en cualquier momento, alterando así los resultados de la prueba.