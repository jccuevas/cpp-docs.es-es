---
title: decay (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- decay
- type_traits/std::decay
dev_langs:
- C++
helpviewer_keywords:
- decay class
ms.assetid: 96baa2fd-c8e0-49af-be91-ba375ba7f9dc
caps.latest.revision: 20
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 51fbd09793071631985720550007dddbe16f598f
ms.openlocfilehash: cb75f00c4f7dfc46122c8e69e5572de1ec23f8ed
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

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




