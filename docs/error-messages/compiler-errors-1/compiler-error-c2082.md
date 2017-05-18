---
title: Error del compilador C2082 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2082
dev_langs:
- C++
helpviewer_keywords:
- C2082
ms.assetid: 87a6d442-157c-46e8-9bff-8388f8338ae0
caps.latest.revision: 8
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
ms.openlocfilehash: 4e31fdadc01983f3ec82e69bf0f4dcfdb682eb6e
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2082"></a>Error del compilador C2082
Nueva definición del parámetro formal 'identifier'  
  
 Un parámetro formal para una función volvió a declararse dentro del cuerpo de función. Para resolver el error, quite la redefinición.  
  
 El ejemplo siguiente genera la advertencia C2082:  
  
```  
// C2082.cpp  
void func(int i) {  
   int i;   // C2082  
   int ii;   // OK  
}  
```
