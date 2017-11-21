---
title: 'CDynamicAccessor:: GetBookmark | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor.GetBookmark
- GetBookmark
- CDynamicAccessor::GetBookmark
- ATL.CDynamicAccessor.GetBookmark
- ATL::CDynamicAccessor::GetBookmark
dev_langs: C++
helpviewer_keywords: GetBookmark method
ms.assetid: 6d0a2970-0c62-4a34-bac7-149d8e990f81
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d9c8f6a2567684ffb7c7faee62cdca501c53ba0c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicaccessorgetbookmark"></a>CDynamicAccessor::GetBookmark
Recupera el marcador de la fila actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT GetBookmark(   
   CBookmark< >* pBookmark    
) const throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pBookmark`  
 [out] Un puntero a la [CBookmark](../../data/oledb/cbookmark-class.md) objeto.  
  
## <a name="return-value"></a>Valor devuelto  
 Uno de los estándar `HRESULT` valores.  
  
## <a name="remarks"></a>Comentarios  
 Es necesario establecer **DBPROP_IRowsetLocate** a `VARIANT_TRUE` para recuperar un marcador.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)