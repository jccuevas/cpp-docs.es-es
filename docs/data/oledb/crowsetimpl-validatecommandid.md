---
title: CRowsetImpl::ValidateCommandID | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs:
- C++
helpviewer_keywords:
- ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f5d3b90ef56ee15e3834c2867a781323689d3054
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
Comprueba para ver si alguno o ambos **DBID**contienen valores de cadena y si es así, los copia a sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CRowsetBaseImpl::ValidateCommandID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pTableID`  
 [in] Un puntero a la **DBID** que representa el identificador de tabla.  
  
 `pIndexID`  
 [in] Un puntero a la **DBID** que representa el identificador de índice.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Se llama a este método a través de una conversión hacia arriba estático por `CRowsetImpl` para rellenar sus miembros de datos [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). De forma predeterminada, este método comprueba para ver si alguno o ambos **DBID**contienen valores de cadena y si es así, los copia a sus miembros de datos. Mediante la colocación de un método con esta firma en el `CRowsetImpl`-clase derivada, se llamará al método en lugar de la implementación base.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CRowsetImpl (clase)](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)