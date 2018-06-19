---
title: Error de compilador Error C3171 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3171
dev_langs:
- C++
helpviewer_keywords:
- C3171
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5ee6ee02511242e2af87024c741a3c97f3f3724d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257056"
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