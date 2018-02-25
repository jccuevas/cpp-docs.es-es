---
title: Clase is_nothrow_default_constructible | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- type_traits/std::is_nothrow_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_nothrow_default_constructible
ms.assetid: c576fcc9-5be1-43aa-b93a-64d3f1848887
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f113e293ea71b6fa60e48091e3b81dbe92554e96
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="isnothrowdefaultconstructible-class"></a>Clase is_nothrow_default_constructible
Comprueba si el tipo tiene un constructor predeterminado que no produce excepciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Ty>
struct is_nothrow_default_constructible;
```  
  
#### <a name="parameters"></a>Parámetros  
 `Ty`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo contiene true si el tipo `Ty` tiene un constructor predeterminado nothrow; en caso contrario, contiene false. Una instancia del predicado de tipo es equivalente a `is_nothrow_constructible<Ty>`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



