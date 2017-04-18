---
title: Error del compilador C2929 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2929
dev_langs:
- C++
helpviewer_keywords:
- C2929
ms.assetid: 11134027-6adc-4733-b6bd-b94486bd1933
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 396f26159fb3852e6329ce9a8ac013c5be65b3bb
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c2929"></a>Error del compilador C2929
'identifier': creación de instancias explícita; no se puede forzar y suprimir de forma explícita la creación de instancias de miembros de clase de plantilla  
  
 No se puede usar con instancias explícitamente un identificador mientras se evita que este se use con instancias.  
  
 El ejemplo siguiente genera la advertencia C2929:  
  
```  
// C2929.cpp  
// compile with: /c  
template<typename T>  
class A {  
public:  
   A() {}  
};  
  
template A<int>::A();  
  
extern template A<int>::A();   // C2929  
```
