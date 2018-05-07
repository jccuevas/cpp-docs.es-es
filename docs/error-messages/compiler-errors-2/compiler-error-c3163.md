---
title: Error del compilador C3163 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3163
dev_langs:
- C++
helpviewer_keywords:
- C3163
ms.assetid: 17dcafa3-f416-4e04-a232-f9569218ba75
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e7be8fbba29cf82070d6fd96c76f810bda961489
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3163"></a>Error del compilador C3163
'construcción': atributos incoherentes con la declaración anterior.  
  
 Los atributos que se aplican a una definición de entrar en conflicto con los atributos que se aplican a una declaración.  
  
 Una manera de resolver el error C3163 es eliminar atributos en la declaración adelantada. Deben ser menor que los atributos en la definición de los atributos en una declaración adelantada o, a lo sumo, igual a estos.  
  
 Una posible causa del error error C3163 implica el lenguaje de anotación de código fuente de Microsoft (SAL). Las macros SAL no se expandan a menos que se compila el proyecto mediante el **/ analyze** marca. Un programa que se compila correctamente sin / analyze podría producir el error C3163 si intenta volver a compilar con la / analyze (opción). Para obtener más información acerca de SAL, consulte [anotaciones SAL](../../c-runtime-library/sal-annotations.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera el error C3163.  
  
```  
// C3163.cpp  
// compile with: /clr /c  
using namespace System;  
  
[CLSCompliant(true)] void f();  
[CLSCompliant(false)] void f() {}   // C3163  
// try the following line instead  
// [CLSCompliant(true)] void f() {}  
```  
  
## <a name="see-also"></a>Vea también  
 [Anotaciones SAL](../../c-runtime-library/sal-annotations.md)