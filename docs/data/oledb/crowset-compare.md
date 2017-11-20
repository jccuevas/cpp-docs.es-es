---
title: 'CRowset:: Compare | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowset<TAccessor>.Compare
- CRowset<TAccessor>::Compare
- ATL.CRowset<TAccessor>.Compare
- ATL::CRowset<TAccessor>::Compare
- CRowset.Compare
- ATL::CRowset::Compare
- ATL.CRowset.Compare
- CRowset::Compare
dev_langs: C++
helpviewer_keywords: Compare method
ms.assetid: a8117b40-7abd-4867-b0ba-eb9e9808204e
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b7ad1f8b153f9f6b546d9781bb4544b13bcc7ce1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetcompare"></a>CRowset::Compare
Compara dos marcadores usando [IRowsetLocate:: Compare](https://msdn.microsoft.com/en-us/library/ms709539.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT Compare(   
   const CBookmarkBase& bookmark1,   
   const CBookmarkBase& bookmark2,   
   DBCOMPARE* pComparison    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Marcador Bookmark1*  
 [in] El primer marcador que se va a comparar.  
  
 *Bookmark2*  
 [in] El segundo marcador que se va a comparar.  
  
 `pComparison`  
 [out] Un puntero al resultado de la comparación.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional `IRowsetLocate`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetLocate** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre el uso de marcadores en los consumidores, consulte [Using Bookmarks](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (Clase)](../../data/oledb/crowset-class.md)