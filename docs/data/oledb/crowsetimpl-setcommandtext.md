---
title: 'CRowsetImpl:: SetCommandText | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.SetCommandText
- CRowsetImpl::SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- SetCommandText method
ms.assetid: e016d7df-c1a0-4dee-b19b-c876680221fd
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 18508fed21bb459f4b4c6a653437b1546c8d1a2b
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="crowsetimplsetcommandtext"></a>CRowsetImpl::SetCommandText
Valida y almacena el **DBID**s en las dos cadenas ([m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) y [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md)).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CRowsetBaseImpl::SetCommandText(DBID* pTableID,  
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
 El **SetCommentText** llama al método `CreateRowset`, una variable static hace plantilla método `IOpenRowsetImpl`.  
  
 Este método delega su trabajo mediante una llamada a [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md) a través de un puntero de conversión hacia arriba.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CRowsetImpl (Clase)](../../data/oledb/crowsetimpl-class.md)