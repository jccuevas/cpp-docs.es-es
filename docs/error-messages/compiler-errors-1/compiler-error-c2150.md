---
title: Error del compilador C2150 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d31a8767f05ba8c58e07ffbabed4e7a96a919e6f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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