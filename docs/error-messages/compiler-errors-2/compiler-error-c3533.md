---
title: Error del compilador C3533 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: faaf53d08512559b86c95148bc93e7b3367d2b01
ms.sourcegitcommit: 3bb7c1c0ceeb8012418e2fff9ae5a7db0fff3877
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
ms.locfileid: "34458919"
---
# <a name="compiler-error-c3533"></a>Error del compilador C3533
'type': un parámetro no puede tener un tipo que contiene 'auto'  
  
 No se puede declarar un parámetro de método o una plantilla con el `auto` palabra clave si el valor predeterminado [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) opción del compilador está en vigor.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Quitar el `auto` palabra clave de la declaración de parámetro.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera C3533 porque declara un parámetro de función con el `auto` palabra clave y se compila con **/Zc: Auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j) {} // C3533  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera C3533 en modo de C ++ 14 porque declara un parámetro de plantilla con el `auto` palabra clave y se compila con **/Zc: Auto**. (En C ++ 17, esta es una definición válida de una plantilla de clase con un parámetro de plantilla sin tipo único cuyo tipo se deduce).
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C {}; // C3533  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)   
 [/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)
