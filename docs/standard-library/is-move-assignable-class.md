---
title: Clase is_move_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_move_assignable
dev_langs: C++
helpviewer_keywords: is_move_assignable
ms.assetid: f33137f2-0639-4912-8745-bc0f9fd18d28
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9fba36cfb8b23a804a6851810294b54bf65c5055
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ismoveassignable-class"></a>Clase is_move_assignable
Comprueba si el tipo se puede asignar mediante movimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct is_move_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Un tipo se puede asignar mediante movimiento si una referencia a un valor R al tipo se puede asignar a una referencia al tipo. El predicado de tipo es equivalente a `is_assignable<T&, T&&>`. Los tipos que se pueden asignar mediante movimiento incluyen tipos escalares a los que se puede hacer referencia y tipos de clase que tienen operadores de asignación de movimiento generados por el compilador o definidos por el usuario.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



