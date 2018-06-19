---
title: Compilador Error C3170 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3170
dev_langs:
- C++
helpviewer_keywords:
- C3170
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8bb077bcad95de0be17e630803b5d4ea9825be61
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33255918"
---
# <a name="compiler-error-c3170"></a>C3170 de Error del compilador
no pueden tener identificadores de módulo distintos en un proyecto  
  
 [módulo](../../windows/module-cpp.md) se encontraron atributos con nombres diferentes en dos de los archivos en una compilación. Solo un único `module` atributo se puede especificar por cada compilación.  
  
 Idénticos `module` atributos se pueden especificar más de un archivo de código fuente.  
  
 Por ejemplo, si se encontraron los siguientes atributos de módulo:  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 Y luego,  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 el compilador generará el error C3170 (Observe los nombres diferentes).