---
title: Clase is_trivial | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- type_traits/std::is_trivial
dev_langs:
- C++
helpviewer_keywords:
- is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: f4e57d84395ebce879187de37c7e2a59f33bfb1b
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="istrivial-class"></a>Clase is_trivial
Comprueba si el tipo es un tipo trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
struct is_trivial;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` es un tipo trivial; en caso contrario, es false. Los tipos triviales son tipos escalares, tipos de clase que se pueden copiar de forma trivial, matrices de estos tipos y versiones de tipo cv-qualified (const, volatile, const volatile) de estos tipos.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)




