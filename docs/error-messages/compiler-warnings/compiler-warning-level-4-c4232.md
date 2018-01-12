---
title: Compilador advertencia (nivel 4) C4232 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4232
dev_langs: C++
helpviewer_keywords: C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: d0b8725ca2a7ee6c5f512559eecdb6b01ac4c6a6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4232"></a>Advertencia del compilador (nivel 4) C4232
ha utilizado una extensión no estándar: 'identificador': la dirección de dllimport 'dllimport' no es estática, no se garantiza la identidad  
  
 En las extensiones de Microsoft (/Ze), se puede indicar un valor no estático como la dirección de una función declarada con el **dllimport** modificador. La compatibilidad con ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)), se produce un error.  
  
 El ejemplo siguiente genera C4232:  
  
```  
// C4232.c  
// compile with: /W4 /Ze /c  
int __declspec(dllimport) f();  
int (*pfunc)() = &f;   // C4232  
```