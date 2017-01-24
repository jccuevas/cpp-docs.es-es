---
title: "Advertencia del compilador (nivel 1) C4420 | Microsoft Docs"
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
  - "C4420"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4420"
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4420
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : operador no disponible, se usa 'operador' en su lugar; la comprobación en tiempo de ejecución puede verse afectada  
  
 Se genera esta advertencia al usar la opción [\/RTCv](../../build/reference/rtc-run-time-error-checks.md) \(comprobación de vector new\/delete\) y cuando no se encuentra ningún tipo de vector.  En este caso, se utiliza la forma que no es de vector.  
  
 Para que la opción \/RTCv funcione correctamente, el compilador siempre debe llamar a la forma vectorial de [new](../../cpp/new-operator-cpp.md)\/[delete](../../cpp/delete-operator-cpp.md) si se utiliza la sintaxis de vectores.