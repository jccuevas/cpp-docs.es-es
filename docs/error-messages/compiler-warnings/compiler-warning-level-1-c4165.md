---
title: Compilador advertencia (nivel 1) C4165 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4165
dev_langs:
- C++
helpviewer_keywords:
- C4165
ms.assetid: f5bed515-2290-4f88-8dab-b45d95fe26ef
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: 9f2007a2f43cd7641979b663c58efb3a8e276246
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4165"></a>Compilador advertencia (nivel 1) C4165
'HRESULT' se está convirtiendo en 'bool'; ¿seguro que desea realizar esta operación?  
  
Cuando se utiliza un valor HRESULT a un [si](../../cpp/if-else-statement-cpp.md) (instrucción), el valor HRESULT se convertirá en un [bool](../../cpp/bool-cpp.md) a menos que se pruebe explícitamente la variable como HRESULT. De forma predeterminada, esta advertencia está desactivada.  
  
## <a name="example"></a>Ejemplo  
El ejemplo siguiente genera C4165  
  
```cpp  
// C4165.cpp  
// compile with: /W1  
#include <windows.h>  
#pragma warning(1:4165)  
  
extern HRESULT hr;  
int main() {  
   if (hr) {  
   // try either of the following ...  
   // if (FAILED(hr)) { // C4165 expected  
   // if (hr != S_OK) {  
   }  
}  
```
