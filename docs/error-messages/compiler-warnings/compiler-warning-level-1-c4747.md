---
title: Compilador advertencia (nivel 1) C4747 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4747
dev_langs: C++
helpviewer_keywords: C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 23c0598c97bf0f2ab05169cb7bf72b9efd5a3f7c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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