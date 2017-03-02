---
title: Compilador advertencia (nivel 1) C4190 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4190
dev_langs:
- C++
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
caps.latest.revision: 7
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
translationtype: Machine Translation
ms.sourcegitcommit: 4ac033535632e94a365aa8dafd849f2ab28a3af7
ms.openlocfilehash: bf45c0737f52da93f93c1f95d313771f0e92a10e
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-warning-level-1-c4190"></a>Compilador advertencia (nivel 1) C4190
'identificador1' tiene una vinculación C especificada, pero devuelve UDT 'identificador2' que es incompatible con C  
  
 Una función o un puntero a función tiene un tipo definido por (definido por el usuario, que es una clase, estructura, enumeración o union) como tipo de valor devuelto y `extern` vinculación "C". Esto está permitido si:  
  
-   Todas las llamadas a esta función tienen lugar desde C++.  
  
-   Es la definición de la función en C++.  
  
## <a name="example"></a>Ejemplo  
  
```cpp  
// C4190.cpp  
// compile with: /W1 /LD  
struct X  
{  
   int i;  
   X ();  
   virtual ~X ();  
};  
  
extern "C" X func ();   // C4190  
```
