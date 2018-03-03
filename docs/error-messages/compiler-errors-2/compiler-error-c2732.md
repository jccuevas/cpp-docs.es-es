---
title: Error de compilador Error C2732 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2732
dev_langs:
- C++
helpviewer_keywords:
- C2732
ms.assetid: 01b7ad2c-93cf-456f-a4c0-c5f2fdc7c07c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aeecaab0fd9faaa6a876aa57781160df6bb26502
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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