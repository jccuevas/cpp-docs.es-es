---
title: Error del compilador C2142 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2142
dev_langs:
- C++
helpviewer_keywords:
- C2142
ms.assetid: d0dbe10e-0952-49a4-8b33-e82fb7558b19
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 3a7e3a8950718ef50c8a497847d72a371f592e59
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2142"></a>Error del compilador C2142
las declaraciones de función son diferentes, los parámetros de variables especificados sólo en uno de ellos  
  
 Una declaración de la función contiene una lista de parámetros variable. Otra declaración no lo hace. ANSI C ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) únicamente.  
  
 El ejemplo siguiente genera C2142:  
  
```  
// C2142.c  
// compile with: /Za /c  
void func();  
void func( int, ... );   // C2142  
void func2( int, ... );   // OK  
```
