---
title: Compilador advertencia (nivel 1) C4228 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4228
dev_langs:
- C++
helpviewer_keywords:
- C4228
ms.assetid: 9301d660-d601-464e-83f5-7ed844a3c6dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 023bf60930a53b6bd881680caebb78c151406df4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276795"
---
# <a name="compiler-warning-level-1-c4228"></a>Advertencia del compilador (nivel 1) C4228
ha utilizado una extensión no estándar: se omiten los calificadores después de coma en la lista de declaradores  
  
 Uso de calificadores como **const** o `volatile` después de una coma al declarar variables es una extensión de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
## <a name="example"></a>Ejemplo  
  
```  
// C4228.cpp  
// compile with: /W1  
int j, const i = 0;  // C4228  
int k;  
int const m = 0;  // ok  
int main()  
{  
}  
```