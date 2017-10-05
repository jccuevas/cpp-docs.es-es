---
title: Clase is_trivially_move_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: d59ca4d7830940a2b99e4e10e885d80842dc7d1b
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="istriviallymoveconstructible-class"></a>Clase is_trivially_move_constructible
Comprueba si el tipo tiene un constructor de movimiento trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_trivially_move_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` es una clase que tiene un constructor de movimiento trivial; en caso contrario, contiene false.  
  
 Un constructor de movimiento para una clase `Ty` es trivial si:  
  
 se declara de forma implícita  
  
 sus tipos de parámetro son equivalentes a los de una declaración implícita  
  
 la clase `Ty` no tiene ninguna función virtual  
  
 la clase `Ty` no tiene ninguna base virtual  
  
 la clase no tiene ningún miembro de datos no estáticos volátil  
  
 todas las bases directas de la clase `Ty` tienen constructores de movimiento trivial  
  
 las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores de movimiento triviales  
  
 las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de movimiento triviales  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




