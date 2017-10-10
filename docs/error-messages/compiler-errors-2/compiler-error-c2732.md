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
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 38b364ac890118ce90164c3003a76e0d3c2e100d
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

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
