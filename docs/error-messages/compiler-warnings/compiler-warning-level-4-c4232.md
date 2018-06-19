---
title: Compilador advertencia (nivel 4) C4232 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4232
dev_langs:
- C++
helpviewer_keywords:
- C4232
ms.assetid: f92028a5-4ddd-43c1-97f5-4f724e5e14af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 093f9eeeb27b402b58f3d53ae34952c34dca3779
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293833"
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