---
title: Error del compilador C2492 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2492
dev_langs:
- C++
helpviewer_keywords:
- C2492
ms.assetid: 8c44c9bb-c366-4fe5-a0ab-882e38608aaa
caps.latest.revision: 10
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
ms.sourcegitcommit: 4bac7b2942f9d72674b8092dc7bf64174dd3c349
ms.openlocfilehash: 54a650e967acb2ee0b6864780823111b4db9414c
ms.contentlocale: es-es
ms.lasthandoff: 04/24/2017

---
# <a name="compiler-error-c2492"></a>Error del compilador C2492
'*variable*': datos con duración de almacenamiento de subprocesos no pueden tener una interfaz dll    
  
 La variable se declara con el [subproceso](../../cpp/thread.md) de atributo y sin el archivo DLL de la interfaz. La dirección de la `thread` variable no se conoce hasta el tiempo de ejecución, por lo que no se puede vincular a una DLL importación o exportación.  
  
 El ejemplo siguiente genera C2492:  
  
```  
// C2492.cpp  
// compile with: /c  
class C {  
public:  
   char   ch;  
};  
  
__declspec(dllexport) __declspec(thread) C c_1;   // C2492  
__declspec(thread) C c_1;   // OK  
```
