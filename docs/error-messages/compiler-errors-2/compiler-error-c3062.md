---
title: Error del compilador C3062 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: da507511cb5f091d5d9432bbfeb36951e3f43c6f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33250571"
---
# <a name="compiler-error-c3062"></a>Error del compilador C3062
'enum': enumerador requiere un valor porque el tipo subyacente es 'type'  
  
 Puede especificar un tipo subyacente de una enumeración. Sin embargo, algunos tipos requieren que se asignen valores a cada enumerador.  
  
 Para obtener más información sobre las enumeraciones, vea [clase enum](../../windows/enum-class-cpp-component-extensions.md).  
  
 El ejemplo siguiente genera C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```