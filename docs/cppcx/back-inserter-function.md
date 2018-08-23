---
title: back_inserter (función) | Microsoft Docs
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: language-reference
f1_keywords:
- collection/Windows::Foundation::Collections::back_inserter
dev_langs:
- C++
helpviewer_keywords:
- back_inserter Function
ms.assetid: 91476338-5548-44b7-bc7e-2150f4fbe31a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6142255c00d9764e4a1a18dab094899b5e9d9e1d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589992"
---
# <a name="backinserter-function"></a>back_inserter (Función)
Devuelve un iterador que se utiliza para insertar elementos en el final de la colección especificada.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
template <typename T>
Platform::BackInsertIterator<T>   
    back_inserter(IVector<T>^ v);  
  
template<typename T>  
Platform::BackInsertIterator<T>   
   back_inserter(IObservableVector<T>^ v);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Un parámetro de tipo de plantilla.  
  
 `v`  
 Un puntero de interfaz que proporciona acceso a la colección subyacente.  
  
### <a name="return-value"></a>Valor devuelto  
 Iterador.  
  
### <a name="requirements"></a>Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Windows::Foundation::Collections  
  
## <a name="see-also"></a>Vea también  
 [Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)