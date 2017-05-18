---
title: Compilador advertencia (nivel 1) C4399 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4399
dev_langs:
- C++
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
caps.latest.revision: 9
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
ms.openlocfilehash: 7d7584e318a42530a2a91fee4b428c92bfaf120c
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4399"></a>Advertencia del compilador (nivel 1) C4399
'símbolo': símbolo por proceso no se debe marcar con __declspec (dllimport) cuando se compila con/CLR: pure  
  
 El **/CLR: pure** opción del compilador está desusada en Visual Studio 2015.  
  
 No se pueden importar datos de una imagen nativa o de una imagen con construcciones nativas y CLR en una imagen pura. Para resolver esta advertencia, compile con **/CLR** (no **/CLR: pure**) o eliminar `__declspec(dllimport)`.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4399.  
  
```  
// C4399.cpp  
// compile with: /clr:pure /doc /W1 /c  
__declspec(dllimport) __declspec(process) extern const int i;   // C4399  
```
