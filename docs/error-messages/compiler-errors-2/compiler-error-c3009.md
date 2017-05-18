---
title: Error del compilador C3009 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3009
dev_langs:
- C++
helpviewer_keywords:
- C3009
ms.assetid: aded5985-f5fd-4c3e-a157-16be55ec1313
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 31c0f8e3c4d9a38174ff8c8aac14908f33ab5e77
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3009"></a>Error del compilador C3009
'label': no se permiten saltos dentro de un bloque estructurado de OpenMP  
  
 No se puede saltar dentro o fuera del código un bloque OpenMP.  
  
 El ejemplo siguiente genera la advertencia C3009:  
  
```  
// C3009.c  
// compile with: /openmp  
int main() {  
   #pragma omp parallel   
   {  
   lbl2:;  
   }  
   goto lbl2;   // C3009  
}  
```
