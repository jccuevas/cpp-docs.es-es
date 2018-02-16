---
title: 'IRowsetImpl:: RestartPosition | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.IRowsetImpl.RestartPosition
- IRowsetImpl::RestartPosition
- RestartPosition
- ATL::IRowsetImpl::RestartPosition
- IRowsetImpl.RestartPosition
dev_langs:
- C++
helpviewer_keywords:
- RestartPosition method
ms.assetid: 14de66ef-8d2c-4404-adb6-3f6c74ac6cf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 5cfdf198b68b3587146ebc4a666ac2e596d05aba
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="irowsetimplrestartposition"></a>IRowsetImpl::RestartPosition
Cambia de posición de la siguiente posición de captura en su posición inicial; es decir, su posición cuando el conjunto de filas fue el primero creado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(RestartPosition )(HCHAPTER /* hReserved */);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IRowset:: RestartPosition](https://msdn.microsoft.com/en-us/library/ms712877.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="remarks"></a>Comentarios  
 La posición del conjunto de filas es indefinida hasta **GetNextRow** se llama. Puede moverse hacia atrás en un rowet mediante una llamada a `RestartPosition` y, a continuación, captura o el desplazamiento hacia atrás.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IRowsetImpl (Clase)](../../data/oledb/irowsetimpl-class.md)