---
title: "Comptr:: CopyTo (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1f47df584fb456c721c92823a87ca525beb052d6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo (Método)
Copias de la interfaz actual o especificada asociada a esta ComPtr al puntero especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  
template<  
   typename U  
>  
  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `U`  
 Nombre de tipo.  
  
 `ptr`  
 Cuando se completa esta operación, un puntero a la interfaz solicitada.  
  
 `riid`  
 Id. de interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que indica el motivo del error de la operación de QueryInterface implícita.  
  
## <a name="remarks"></a>Comentarios  
 La primera función devuelve una copia de un puntero a la interfaz asociada a esta ComPtr. Esta función siempre devuelve S_OK.  
  
 La segunda función realiza una operación de QueryInterface en la interfaz asociada a esta ComPtr de la interfaz especificada por el `riid` parámetro.  
  
 La tercera función realiza una operación de QueryInterface en la interfaz asociada a esta ComPtr de la interfaz subyacente de la `U` parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)