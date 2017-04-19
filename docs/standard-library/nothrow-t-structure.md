---
title: nothrow_t (Estructura) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- nothrow_t
dev_langs:
- C++
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
caps.latest.revision: 20
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
ms.sourcegitcommit: 85c900f2263ae1c1089478badc85388e3b5e8548
ms.openlocfilehash: b490cccf048b5d5b9be53508331cba89e66c952f
ms.lasthandoff: 02/24/2017

---
# <a name="nothrowt-structure"></a>nothrow_t (Estructura)
El struct que se usa como parámetro de función del operador new para indicar que la función debe devolver un puntero nulo para notificar un error de asignación, en lugar de producir una excepción.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct std::nothrow_t {};
```  
  
## <a name="remarks"></a>Comentarios  
 El struct ayuda al compilador a seleccionar la versión correcta del constructor. [nothrow](../standard-library/new-functions.md#nothrow) es un sinónimo de objetos de tipo `std::nothrow_t`.  
  
## <a name="example"></a>Ejemplo  
 Vea [operator new](../standard-library/new-operators.md#operator_new) y [operator new&#91;&#93;](../standard-library/new-operators.md#operator_new_arr) para obtener ejemplos de cómo se usa `std::nothrow_t` como un parámetro de función.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<new>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)




