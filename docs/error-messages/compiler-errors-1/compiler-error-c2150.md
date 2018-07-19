---
title: Error del compilador C2150 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7dc7a84ff666fdc17f0abeec690a548f216ce975
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170153"
---
# <a name="compiler-error-c2150"></a>Error del compilador C2150
  
> '*identificador*': campo de bits debe tener el tipo 'int', 'signed int' o 'unsigned int'  
  
 El tipo base para un campo de bits debe ser `int`, `signed int`, o `unsigned int`.  
  
## <a name="example"></a>Ejemplo  
  
 Este ejemplo muestra cómo podría encontrar la advertencia C2150 y cómo corregirlo:  
  
```cpp  
// C2150.cpp  
// compile with: /c  
struct A {  
   float a : 8;    // C2150  
   int i : 8;      // OK  
};  
```