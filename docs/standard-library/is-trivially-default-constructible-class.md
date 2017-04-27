---
title: Clase is_trivially_default_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- is_trivially_default_constructible
- type_traits/std::is_trivially_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_default_constructible
ms.assetid: 653ecd73-909f-4dd8-b95a-d1164d1c2da4
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: dd41fbdcc33250bc60a0b919b17dd52862549a77
ms.lasthandoff: 02/24/2017

---
# <a name="istriviallydefaultconstructible-class"></a>is_trivially_default_constructible (clase)
Comprueba si el tipo tiene un constructor predeterminado trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_trivially_default_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `Ty` es una clase que tiene un constructor trivial; en caso contrario, es false.  
  
 Un constructor predeterminado para una clase `Ty` es trivial si:  
  
-   es un constructor predeterminado declarado implícitamente  
  
-   la clase `Ty` no tiene ninguna función virtual  
  
-   la clase `Ty` no tiene ninguna base virtual  
  
-   todas las bases directas de la clase `Ty` tienen constructores triviales  
  
-   las clases de todos los miembros de datos no estáticos del tipo de clase tienen constructores triviales  
  
-   las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores triviales  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




