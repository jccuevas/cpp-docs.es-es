---
title: Error del compilador C3279 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3279
dev_langs:
- C++
helpviewer_keywords:
- C3279
ms.assetid: 639afc20-984c-4a95-be35-8bf9409f02d5
caps.latest.revision: 9
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
ms.openlocfilehash: cd0e6c10a544cf9b23edd93a4268122135adb6af
ms.contentlocale: es-es
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3279"></a>Error del compilador C3279
no se permiten especializaciones parciales o explícitas ni creaciones de instancias explícitas de plantillas de clase declaradas en el espacio de nombres cli  
  
 El espacio de nombres `cli` está definido por Microsoft y contiene pseudoplantillas. El compilador de Visual C++ no permite las especializaciones definidas por el usuario, parciales, explícitas ni creaciones de instancias explícitas de plantillas de clase en este espacio de nombres.  
  
 El ejemplo siguiente genera la advertencia C3279:  
  
```  
// C3279.cpp  
// compile with: /clr  
namespace cli {  
   template <> ref class array<int> {};   // C3279  
   template <typename T> ref class array<T, 2> {};   // C3279  
}  
```
