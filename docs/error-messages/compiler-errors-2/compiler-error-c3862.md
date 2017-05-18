---
title: C3862 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3862
dev_langs:
- C++
helpviewer_keywords:
- C3862
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 6
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
ms.sourcegitcommit: cc82b83860786ffc3f0aee73ede18ecadef16a7a
ms.openlocfilehash: 48dbae62c367616a437db0607d84fa89e8006021
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c3862"></a>Error del compilador C3862
'función': no se puede compilar una función no administrada con/CLR: pure o/CLR: safe  
  
 El **/CLR: pure** y **/CLR: safe** opciones del compilador están desusadas en Visual Studio 2015.  
  
 Una compilación con **/CLR: pure** o **/CLR: safe** generará una imagen de MSIL, una imagen sin código nativo (no administrado).  Por lo tanto, no puede utilizar el `unmanaged` pragma en una **/CLR: pure** o **/CLR: safe** compilación.  
  
 Para obtener más información, consulte [/clr (compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md) y [managed, unmanaged](../../preprocessor/managed-unmanaged.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3862:  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```
