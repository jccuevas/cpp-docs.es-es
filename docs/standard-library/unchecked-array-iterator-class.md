---
title: unchecked_array_iterator (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- stdext::unchecked_array_iterator
dev_langs:
- C++
ms.assetid: 693b3b30-4e3a-465b-be06-409700bc50b1
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 02d95c517f6e4af3cd519f05b0ab9c1469c63241
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="uncheckedarrayiterator-class"></a>unchecked_array_iterator (Clase)
La clase `unchecked_array_iterator` permite ajustar una matriz o un puntero en un iterador no comprobado. Use esta clase como contenedor (mediante la función [make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)) para punteros o matrices sin formato como una manera dirigida de administrar advertencias de puntero no comprobadas en lugar de silenciar de manera global estas advertencias. Si es posible, use la versión comprobada de esta clase, [checked_array_iterator](../standard-library/checked-array-iterator-class.md).  
  
> [!NOTE]
>  Esta clase es una extensión de Microsoft de la Biblioteca estándar de C++. El código implementado mediante esta función no es portable a los entornos de compilación estándar de C++ que no admiten esta extensión de Microsoft.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Iterator>  
class unchecked_array_iterator;
```  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se define en el espacio de nombres [stdext](../standard-library/stdext-namespace.md).  
  
 Esta es la versión no comprobada de la [clase checked_array_iterator](../standard-library/checked-array-iterator-class.md) y admite las mismas sobrecargas y los mismos miembros. Para más información sobre la característica de iterador activado con ejemplos de código, vea [Iteradores activados](../standard-library/checked-iterators.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<iterator>  
  
 **Espacio de nombres:** stdext  
  
## <a name="see-also"></a>Vea también  
 [\<iterator>](../standard-library/iterator.md)   
 [Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)



