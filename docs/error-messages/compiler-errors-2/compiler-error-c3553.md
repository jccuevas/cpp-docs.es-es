---
title: Error del compilador C3553 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3553
dev_langs:
- C++
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3a4ed8c2776015f9d9c6aedbe7a9da93f404f680
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3553"></a>Error del compilador C3553
decltype espera una expresión, no un tipo  
  
 La palabra clave `decltype()` requiere una expresión como argumento, no el nombre de un tipo. Por ejemplo, la última instrucción del siguiente fragmento de código genera el error C3553.  
  
 `int x = 0;`  
  
 `decltype(x+1);`  
  
 `decltype(int); // C3553`