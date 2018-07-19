---
title: Error del compilador C3462 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3462
dev_langs:
- C++
helpviewer_keywords:
- C3462
ms.assetid: 56b75f35-9fad-42d9-a969-eeca5d709bec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bb5cfe5bc95c3530746bf263e340c5e3923abb42
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33254185"
---
# <a name="compiler-error-c3462"></a>Error del compilador C3462
'tipo': solamente se puede reenviar un tipo importado.  
  
 El atributo TypeForwardedTo debe aplicarse a un tipo de los metadatos a los que se hace referencia.  
  
 Para obtener más información, consulte [Type Forwarding (C++ / CLI)](../../windows/type-forwarding-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 En el ejemplo siguiente se crea un componente.  
  
```  
// C3462.cpp  
// compile with: /clr /LD  
public ref class R {};  
```  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C3462.  
  
```  
// C3462b.cpp  
// compile with: /clr /c  
#using "C3462.dll"  
ref class N {};  
[assembly:TypeForwardedTo(N::typeid)];   // C3462  
[assembly:TypeForwardedTo(R::typeid)];  
```