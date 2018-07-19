---
title: 'Comptr:: CopyTo (método) | Documentos de Microsoft'
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
ms.openlocfilehash: 680c1278ca2b17c7ea35e72946fb5d5030c5e7c0
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33870876"
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

template<typename U>  
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