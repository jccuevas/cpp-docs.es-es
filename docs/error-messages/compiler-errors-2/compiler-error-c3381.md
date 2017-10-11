---
title: Error del compilador C3381 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 6b1a56658874eb5a62db7d272b40612e34bfc94a
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3381"></a>Error del compilador C3381
'ensamblado' : los especificadores de acceso al ensamblado sólo están disponibles en el código compilado con la opción /clr  
  
 Tipos nativos son visibles fuera del ensamblado, pero solo se puede especificar acceso de ensamblado para tipos nativos en una **/CLR** compilación.  
  
 Para obtener más información, consulte [escriba visibilidad](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera del C3381.  
  
```  
// C3381.cpp  
// compile with: /c  
public class A {};   // C3381  
```
