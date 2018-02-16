---
title: "to_vector (función) | Documentos de Microsoft"
ms.custom: 
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::to_vector
dev_langs:
- C++
helpviewer_keywords:
- to_vector Function
ms.assetid: 9cdd5123-7243-4def-a1d3-162e0bf6219e
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 028acf4b3b049f13c7a9ac2204157432fa144caa
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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
 [Windows::Foundation::Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)