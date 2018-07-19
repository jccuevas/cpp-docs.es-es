---
title: Error del compilador C3707 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3707
dev_langs:
- C++
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7268f584d9f269b4f2f15b837379ec12ab0185d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273730"
---
# <a name="compiler-error-c3707"></a>Error del compilador C3707
'función': el método dispinterface debe tener un dispid  
  
 Si utiliza un `dispinterface` método, se le debe asignar un `dispid`. Para corregir este error, asigne un `dispid` a la `dispinterface` método, por ejemplo, quitando el comentario de la `id` atributo en el método en el ejemplo siguiente. Para obtener más información, vea los atributos [dispinterface](../../windows/dispinterface.md) y [identificador](../../windows/id.md).  
  
 El ejemplo siguiente genera C3707:  
  
```  
// C3707.cpp  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlctl.h>  
  
[module(name="xx")];  
[dispinterface]  
__interface IEvents : IDispatch  
{  
   HRESULT event1([in] int i);   // C3707  
   // try the following line instead  
   // [id(1)] HRESULT event1([in] int i);  
};  
  
int main() {  
}  
```