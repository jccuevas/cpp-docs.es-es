---
title: Error del compilador C3381 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a27961694bc5fad4080d8aceaf2f1cb65404319c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33251103"
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