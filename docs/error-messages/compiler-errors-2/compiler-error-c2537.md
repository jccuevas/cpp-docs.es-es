---
title: Error del compilador C2537 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2537
dev_langs: C++
helpviewer_keywords: C2537
ms.assetid: aee81d8e-300e-4a8b-b6c4-b3828398b34e
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 610fe53b68ccfa9f0ec187356a737e67837656a4
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2537"></a>Error del compilador C2537
'especificador': especificación de vinculación no válida  
  
 Causas posibles:  
  
1.  No se admite el especificador de vinculación. Se admite solo el especificador de vinculación "C".  
  
2.  Vinculación de "C" se especifica más de una función de un conjunto de funciones sobrecargadas. Esto no está permitido.  
  
 El ejemplo siguiente genera C2537:  
  
```  
// C2537.cpp  
// compile with: /c  
extern "c" void func();   // C2537  
extern "C" void func2();   // OK  
```