---
title: C2006 de Error del compilador | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2006
dev_langs:
- C++
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 93880e7d767de3101cd7a292af5fa2874cae86bf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33165576"
---
# <a name="compiler-error-c2006"></a>C2006 de Error del compilador
'directiva' esperaba un nombre de archivo, que se encontró 'token'  
  
 Directivas como [#include](../../preprocessor/hash-include-directive-c-cpp.md) o [#import](../../preprocessor/hash-import-directive-cpp.md) requieren un nombre de archivo. Para resolver el error, asegúrese de que *token* es un nombre de archivo válido. Además, puede colocar el nombre de archivo dobles comillas o corchetes angulares.  
  
 El ejemplo siguiente genera C2006:  
  
```  
// C2006.cpp  
#include stdio.h   // C2006  
```  
  
 Posible resolución:  
  
```  
// C2006b.cpp  
// compile with: /c  
#include <stdio.h>  
```