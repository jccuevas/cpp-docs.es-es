---
title: Compilador advertencia (nivel 1) C4747 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7ecbfe8e2ace06cb6e667d77d315f544ce0b451c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4747"></a>Advertencia del compilador (nivel 1) C4747
Llamada 'entrypoint' administrado: no se puede ejecutar código administrado bajo el bloqueo del cargador, incluido el punto y las llamadas llegadas desde el punto de entrada DLL  
  
 El compilador encontró un (probable) punto de entrada DLL compilado en MSIL.  Debido a posibles problemas con la carga de un archivo DLL cuyo punto de entrada se ha compilado en MSIL, se recomienda encarecidamente no se compile una función de punto de entrada DLL en MSIL.  
  
 Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) y [Error de las herramientas del vinculador LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No compile el módulo con **/CLR**.  
  
2.  Marque la función de punto de entrada con `#pragma unmanaged`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4747.  
  
```  
// C4747.cpp  
// compile with: /clr /c /W1  
// C4747 expected  
#include <windows.h>  
  
// Uncomment the following line to resolve.  
// #pragma unmanaged  
  
BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {  
   return TRUE;  
};  
```
