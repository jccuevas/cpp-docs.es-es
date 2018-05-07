---
title: Error de compilador Error C2732 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef2faf21eb6f0c73d02ea32c7d4ed53f86eec3de
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2732"></a>Error C2732 de Error del compilador
la especificación de vinculación se contradice con la especificación anterior para 'function'  
  
 La función ya se ha declarado con otro especificador de vinculación.  
  
 Este error puede deberse a archivos de inclusión con otros especificadores de vinculación.  
  
 Para corregir este error, cambie las instrucciones `extern` para que las vinculaciones coincidan. En concreto, no incluya directivas `#include` en bloques `extern "C"`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C2732:  
  
```  
// C2732.cpp  
extern void func( void );   // implicit C++ linkage  
extern "C" void func( void );   // C2732  
```