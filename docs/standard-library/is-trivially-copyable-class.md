---
title: Clase is_trivially_copyable | Microsoft Docs
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
- type_traits/std::is_trivially_copyable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_copyable
ms.assetid: 89a53bf8-036c-4108-91e1-fe34adbde8b3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6f3cf5f6ca0fc6168c061df2ec276f058abea51
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="istriviallycopyable-class"></a>Clase is_trivially_copyable
Comprueba si el tipo se puede copiar de forma trivial.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>
struct is_trivially_copyable;
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Tipo que se va a consultar.  
  
## <a name="remarks"></a>Comentarios  
 Una instancia del predicado de tipo es true si el tipo `T` se puede copiar de forma trivial; en caso contrario, es false. Los tipos que se pueden copiar de forma trivial no tienen operaciones de copia, operaciones de movimiento ni destructores no triviales. Por lo general, una operación de copia se considera trivial si se puede implementar como una copia bit a bit. Tanto las matrices de tipos que se pueden copiar de forma trivial como los tipos integrados se pueden copiar de forma trivial.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<type_traits>  
  
 **Espacio de nombres:** std  
  
## <a name="see-also"></a>Vea también  
 [<type_traits>](../standard-library/type-traits.md)



