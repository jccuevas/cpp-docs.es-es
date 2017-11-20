---
title: Error del compilador C3644 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3644
dev_langs: C++
helpviewer_keywords: C3644
ms.assetid: 2e3f6c41-3ec5-4a01-82bc-f11b61ebe68e
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6d4520b382a955bba04802c523faf866b1bf6e4b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3644"></a>Error del compilador C3644
'función': no se puede compilar la función para generar código administrado  
  
 La presencia de algunas palabras clave en una función hará que la función que se va a compilar en código nativo.  
  
 El ejemplo siguiente genera C3644:  
  
```  
// C3644.cpp  
// compile with: /clr  
// processor: x86  
  
void __clrcall Func2(int i) {  
   __asm {}   // C3644  
}  
```