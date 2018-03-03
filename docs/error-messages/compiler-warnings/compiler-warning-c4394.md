---
title: Advertencia del compilador C4394 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6ab51a4f818e8eb8a94150424124a5c96ebaf241
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-c4394"></a>Advertencia del compilador C4394
'función': el símbolo por AppDomain no se debe marcar con __declspec(dllexport)  
  
 Una función marcada con el [appdomain](../../cpp/appdomain.md) `__declspec` modificador se compila en MSIL (no en código nativo) y tablas de exportación ([exportar](../../windows/export.md) `__declspec` modificador) no se admiten para las funciones administradas.  
  
 Puede declarar una función administrada para tener accesibilidad pública. Para obtener más información, consulte [escriba visibilidad](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) y [visibilidad de miembros](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).  
  
 La advertencia C4394 siempre se emite como error.  Puede desactivar esta advertencia con el `#pragma warning` o **/wd**; vea [advertencia](../../preprocessor/warning.md) o  [ /w, / W0, /W1, /W2, /W3, / W4, /w1, /w2, /w3, / W4, / Wall, /wd, / se, /wo, / wv, /WX (nivel de advertencia)](../../build/reference/compiler-option-warning-level.md)para obtener más información.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4394.  
  
```  
// C4394.cpp  
// compile with: /clr /c  
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394  
__declspec(dllexport) int g2 = 0;   // OK  
```