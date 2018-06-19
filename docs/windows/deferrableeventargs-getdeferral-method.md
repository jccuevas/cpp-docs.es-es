---
title: 'Método deferrableeventargs:: Getdeferral | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ef6dc7c5-b0be-4b85-8507-d3fd97f2185d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2442894c5f7bd85eb94262e776294c1e52a19e01
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33883546"
---
# <a name="deferrableeventargsgetdeferral-method"></a>Método DeferrableEventArgs::GetDeferral
Obtiene una referencia a la [aplazamiento](http://go.microsoft.com/fwlink/p/?linkid=526520) el objeto que representa un evento diferido.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT GetDeferral([out, retval] Windows::Foundation::IDeferral** result)  
```  
  
#### <a name="parameters"></a>Parámetros  
 `result`  
 Un puntero que hará referencia a la [aplazamiento](http://go.microsoft.com/fwlink/p/?linkid=526520) objeto cuando se complete la llamada.  
  
## <a name="return-value"></a>Valor devuelto  
 S_OK si se realiza correctamente; de lo contrario, un HRESULT que indica el error.  
  
## <a name="remarks"></a>Comentarios  
 Para obtener un ejemplo de código, vea [clase DeferrableEventArgs](../windows/deferrableeventargs-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** event.h  
  
 **Espacio de nombres:** Microsoft::WRL  
  
## <a name="see-also"></a>Vea también  
 [DeferrableEventArgs (clase)](../windows/deferrableeventargs-class.md)