---
title: to_vector (función) | Documentos de Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0c345b594c284c1273a080d979cd9588aff350d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="tovector-function"></a>to_vector (Función)
Devuelve un objeto `std::vector` cuyo valor es igual que la colección que subyace al parámetro de IVector o de IVectorView especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
template <typename T>  
inline ::std::vector<T> to_vector(IVector<T>^ v); 
 
template <typename T>  
inline ::std::vector<T> to_vector(IVectorView<T>^ v);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El parámetro de tipo de plantilla.  
  
 `v`  
 Una interfaz IVector o IVectorView que proporciona acceso a un objeto Vector o VectorView subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Vea también  
 [Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)