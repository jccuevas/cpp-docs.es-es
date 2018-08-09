---
title: CopyTo (método) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: 8801bc49-6db4-4393-a55f-a701ae3b8718
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 5b387d52c9ab7b1d9033ce70d36e9f0aa5e5b33e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642934"
---
# <a name="comptrcopyto-method"></a>ComPtr::CopyTo (Método)
Copia de la interfaz actual o especificada asociada a este **ComPtr** para el puntero especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT CopyTo(  
   _Deref_out_ InterfaceType** ptr  
);  
  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ void** ptr  
) const;  

template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 *U*  
 Nombre de tipo.  
  
 *ptr*  
 Cuando se completa esta operación, un puntero a la interfaz solicitada.  
  
 *riid*  
 Id. de interfaz.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; en caso contrario, un valor HRESULT que indica por qué implícito `QueryInterface` error en la operación.  
  
## <a name="remarks"></a>Comentarios  
 La primera función devuelve una copia de un puntero a la interfaz asociada a este **ComPtr**. Esta función siempre devuelve S_OK.  
  
 La segunda función realiza una `QueryInterface` operación en la interfaz asociada a este **ComPtr** para la interfaz especificada por el *riid* parámetro.  
  
 La tercera función realiza una `QueryInterface` operación en la interfaz asociada a este **ComPtr** para la interfaz subyacente de la *U* parámetro.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** client.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [ComPtr (clase)](../windows/comptr-class.md)