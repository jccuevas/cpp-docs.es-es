---
title: Clase is_trivially_copy_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- type_traits/std::is_trivially_copy_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: 24
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
ms.openlocfilehash: 3c99808198c527fb60105d9a2d5629d177da5461
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible (Clase)
Comprueba si el tipo tiene un constructor de copia trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct is_trivially_copy_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` es una clase que tiene un constructor de copias trivial; en caso contrario, es false.  
  
 Un constructor de copia para una clase `T` es trivial si se declara implícitamente, la clase `T` no tiene funciones virtuales o bases virtuales, todas las bases directas de la clase `T` tienen constructores de copia triviales, las clases de todos los miembros de datos no estáticos de tipo de clase tienen constructores de copia triviales y las clases de todos los miembros de datos no estáticos de la matriz de tipo de clase tienen constructores de copia triviales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




