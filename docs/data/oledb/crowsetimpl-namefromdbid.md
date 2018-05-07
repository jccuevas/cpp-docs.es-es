---
title: 'CRowsetImpl:: Namefromdbid | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl.NameFromDBID
- CRowsetImpl::NameFromDBID
dev_langs:
- C++
helpviewer_keywords:
- NameFromDBID method
ms.assetid: 6aa5b074-90c7-4434-adfd-c64c13e76c78
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 54ee345d4bf97c6f77398e62d1cb31614868a568
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="crowsetimplnamefromdbid"></a>CRowsetImpl::NameFromDBID
Extrae una cadena de un **DBID** y lo copia en el `bstr` pasado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CRowsetBaseImpl::NameFromDBID(DBID* pDBID,  
   CComBSTR& bstr,  
   bool bIndex);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pDBID*  
 [in] Un puntero a la **DBID** desde el que se va a extraer de una cadena.  
  
 `bstr`  
 [in] A [CComBSTR](../../atl/reference/ccombstr-class.md) referencia para colocar una copia de la **DBID** cadena.  
  
 `bIndex`  
 [in] **true** si un índice **DBID**; **false** si una tabla **DBID**.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar. Dependiendo de si la **DBID** es una tabla o un índice (indicado por `bIndex`), el método le: devolución **DB_E_NOINDEX** o **DB_E_NOTABLE**.  
  
## <a name="remarks"></a>Comentarios  
 Este método es invocado por el `CRowsetImpl` las implementaciones de [ValidateCommandID](../../data/oledb/crowsetimpl-validatecommandid.md) y [GetCommandFromID](../../data/oledb/crowsetimpl-getcommandfromid.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [CRowsetImpl (Clase)](../../data/oledb/crowsetimpl-class.md)