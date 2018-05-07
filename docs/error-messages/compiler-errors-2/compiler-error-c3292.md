---
title: Error del compilador C3292 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3292
dev_langs:
- C++
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 55a7f91bb9d47f2675525cf17096deddae30be71
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3292"></a>Error del compilador C3292
el espacio de nombres cli no se puede abrir de nuevo  
  
 El espacio de nombres cli no se puede declarar en su código.  Para obtener más información, consulte [plataforma, predeterminado y cli espacios de nombres](../../windows/platform-default-and-cli-namespaces-cpp-component-extensions.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3292.  
  
```  
// C3292.cpp  
// compile with: /clr /c  
namespace cli {};   // C3292  
```