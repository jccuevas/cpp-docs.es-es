---
title: Error del compilador C3533 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e7bcd9c710ac5cdd50b966a72291918459d984be
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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