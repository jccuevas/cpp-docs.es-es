---
title: Error de compilador Error C3171 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ebd64aa2c80f6e21b1e5c1829d8e165d46207718
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3171"></a>Error de C3171 de Error de compilador
'module': no se puede especificar atributos module distintos en un proyecto  
  
 [módulo](../../windows/module-cpp.md) se encontraron atributos con listas de parámetros diferentes en dos de los archivos en una compilación. Solo un único `module` atributo se puede especificar por cada compilación.  
  
 Idénticos `module` atributos se pueden especificar más de un archivo de código fuente.  
  
 Por ejemplo, si el siguiente `module` se encontraron atributos:  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 Y luego,  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 el compilador generará el error C3171 (Observe los diferentes valores de versión).
