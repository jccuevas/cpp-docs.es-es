---
title: 'CEnumerator:: Open | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs: C++
helpviewer_keywords: Open method
ms.assetid: b22821a0-257a-4543-ad0c-2649d4ac092e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cf1205fce9466117a3374ebfd18e21cd034ae229
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cenumeratoropen"></a>CEnumerator::Open
Enlaza el moniker del enumerador, si uno se especifica, recupera el conjunto de filas del enumerador mediante una llamada a [ISourcesRowset:: GetSourcesRowset](https://msdn.microsoft.com/en-us/library/ms711200.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT Open(   
   LPMONIKER pMoniker    
) throw( );  
HRESULT Open(   
   const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR    
) throw( );  
HRESULT Open(   
   const CEnumerator& enumerator    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pMoniker`  
 [in] Un puntero a un moniker para un enumerador.  
  
 *pTypeInfo*  
 [in] Un puntero a la **CLSID** del enumerador.  
  
 `enumerator`  
 [in] Una referencia a un enumerador.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CEnumerator (Clase)](../../data/oledb/cenumerator-class.md)