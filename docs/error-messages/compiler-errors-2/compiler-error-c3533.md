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
ms.openlocfilehash: f184f0459e7ec2251d6ff34e2ee76559fe0dea42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3533"></a>Error del compilador C3533
'type': un parámetro no puede tener un tipo que contiene 'auto'  
  
 No se puede declarar un parámetro de método o una plantilla con el `auto` palabra clave si el valor predeterminado [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) opción del compilador está en vigor.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  Quitar el `auto` palabra clave de la declaración de parámetro.  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque se declara un parámetro de función con el `auto` palabra clave y se compila con **/Zc: Auto**.  
  
```  
// C3533a.cpp  
// Compile with /Zc:auto  
void f(auto j){} // C3533  
```  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se genera el error C3535 porque se declara un parámetro de plantilla con el `auto` palabra clave y se compila con **/Zc: Auto**.  
  
```  
// C3533b.cpp  
// Compile with /Zc:auto  
template<auto T> class C{}; // C3533  
```  
  
## <a name="see-also"></a>Vea también  
 [Auto (palabra clave)](../../cpp/auto-keyword.md)   
 [/Zc:auto (Deducir tipo de variable)](../../build/reference/zc-auto-deduce-variable-type.md)