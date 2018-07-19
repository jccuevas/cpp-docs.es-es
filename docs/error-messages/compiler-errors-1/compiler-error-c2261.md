---
title: Error del compilador C2261 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2261
dev_langs:
- C++
helpviewer_keywords:
- C2261
ms.assetid: 60969482-9e83-49b5-9631-a04bc844da12
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 45050daf3149cd813fb23b5814be5fe49c375f03
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33170471"
---
# <a name="compiler-error-c2261"></a>Error del compilador C2261
'string': referencia de ensamblado no es válida y no se puede resolver  
  
 Un valor no era válido.  
  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> se utiliza para especificar un ensamblado de confianza. Por ejemplo, si a.dll desea especificar b.dll como un ensamblado de confianza, podría especificar (en.dll): InternalsVisibleTo("b"). El tiempo de ejecución, a continuación, permite b.dll tenga acceso a todo el contenido de.dll (excepto los tipos privados).  
  
 Para obtener más información sobre la sintaxis correcta al especificar los ensamblados de confianza, consulte [ensamblados Friend (C++)](../../dotnet/friend-assemblies-cpp.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera del C2261.  
  
```  
// C2261.cpp  
// compile with: /clr /c  
using namespace System::Runtime::CompilerServices;  
[assembly: InternalsVisibleTo("a,a,a")];   // C2261  
[assembly: InternalsVisibleTo("a.a")];   // OK  
[assembly: InternalsVisibleTo("a")];   // OK  
```