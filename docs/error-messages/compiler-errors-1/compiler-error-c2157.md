---
title: Error del compilador C2157 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2157
dev_langs: C++
helpviewer_keywords: C2157
ms.assetid: babbca24-16dc-4b69-be14-a675029249c1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5735d0394be8114f2e0747e7e0d8dfefc84e580b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2157"></a>Error del compilador C2157
'function': se debe declarar antes de usarse en la lista pragma  
  
 El nombre de función no se declara antes de que se le haga referencia en la lista de funciones de una pragma [alloc_text](../../preprocessor/alloc-text.md) .  
  
 El ejemplo siguiente genera la advertencia C2157:  
  
```  
// C2157.cpp  
// compile with: /c  
#pragma alloc_text( "func", func)   // C2157  
  
// OK  
extern "C" void func();  
#pragma alloc_text( "func", func)  
```