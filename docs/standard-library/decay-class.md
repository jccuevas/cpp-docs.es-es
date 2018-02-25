---
title: decay (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43ee8ff7971af3026066b3483de4808ec2dc114
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="decay-class"></a>decay (Clase)
Genera el tipo tal y como se pasa por valor. Crea el tipo sin referencia, no constante y no volátil, o crea un puntero al tipo a partir de una función o un tipo de matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct decay;

template <class T>  
using decay_t = typename decay<T>::type;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a modificar.  
  
## <a name="remarks"></a>Comentarios  
 Use la plantilla decay para producir el tipo resultante como si el tipo se hubiera pasado por valor como un argumento. El typedef de miembro de clase de plantilla `type` contiene un tipo modificado que se define en las siguientes fases:  
  
-   El tipo `U` se define como `remove_reference<T>::type`.  
  
-   Si `is_array<U>::value` es True, el tipo modificado `type` es `remove_extent<U>::type *`.  
  
-   De lo contrario, si `is_function<U>::value` es True, el tipo modificado `type` es `add_pointer<U>::type`.  
  
-   De lo contrario, el tipo modificado `type` es `remove_cv<U>::type`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



