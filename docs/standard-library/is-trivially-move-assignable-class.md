---
title: Clase is_trivially_move_assignable | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 32cfcd78cdc57e9ac0c238a3046d034d5d97f114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="istriviallymoveassignable-class"></a>Clase is_trivially_move_assignable
Comprueba si el tipo tiene un operador de asignación de movimiento trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_trivially_move_assignable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un operador de asignación de movimiento trivial; en caso contrario, contiene false.  
  
 Un operador de asignación de movimiento para una clase `Ty` es trivial si:  
  
 se proporciona de forma implícita  
  
 la clase `Ty` no tiene ninguna función virtual  
  
 la clase `Ty` no tiene ninguna base virtual  
  
 las clases de todos los miembros de datos no estáticos del tipo de clase tienen operadores de asignación de movimiento triviales  
  
 las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen operadores de asignación de movimiento triviales  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



