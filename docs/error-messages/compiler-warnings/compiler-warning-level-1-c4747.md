---
title: Compilador advertencia (nivel 1) C4747 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 203943f3741d07e278652a7032a6dcdcb305a384
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33285829"
---
# <a name="compiler-warning-level-1-c4747"></a>Advertencia del compilador (nivel 1) C4747
Al llamar a 'entrypoint' administrado: no se puede ejecutar código administrado en un bloqueo del cargador, incluido el punto de entrada DLL y las llamadas alcanzadas desde el punto de entrada DLL  
  
 El compilador encontró un punto de entrada DLL (probable) compilado en MSIL.  Debido a posibles problemas al cargar un archivo DLL cuyo punto de entrada se ha compilado en MSIL, se recomienda encarecidamente no se compile una función de punto de entrada DLL en MSIL.  
  
 Para obtener más información, consulte [inicialización de ensamblados mixtos](../../dotnet/initialization-of-mixed-assemblies.md) y [Error de error herramientas del vinculador LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
1.  No se compile el módulo con **/CLR**.  
  
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