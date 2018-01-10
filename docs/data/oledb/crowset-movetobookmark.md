---
title: 'CRowset:: MoveToBookmark | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CRowset::MoveToBookmark
- ATL::CRowset<TAccessor>::MoveToBookmark
- ATL.CRowset.MoveToBookmark
- ATL.CRowset<TAccessor>.MoveToBookmark
- MoveToBookmark
- CRowset::MoveToBookmark
- CRowset.MoveToBookmark
- CRowset<TAccessor>::MoveToBookmark
dev_langs: C++
helpviewer_keywords: MoveToBookmark method
ms.assetid: 90124723-8daf-4692-ae2f-0db26b5db920
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 08e570d6d2cbc8c5943ce0591c280b74be573e2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovetobookmark"></a>CRowset::MoveToBookmark
Recopila la fila marcada por fila en un desplazamiento especificado o un marcador (`lSkip`) de ese marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT MoveToBookmark(   
   const CBookmarkBase& bookmark,   
   LONG lSkip = 0    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bookmark`  
 [in] Un marcador marcar la ubicación desde la que va a capturar datos.  
  
 `lSkip`  
 [in] El recuento de número de filas de marcador a la fila de destino. Si `lSkip` es cero, la primera fila es la fila marcada. Si `lSkip` es 1, la primera fila es la fila después de la fila marcada. Si `lSkip` es -1, la primera fila es la fila antes de la fila marcada.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar.  
  
## <a name="remarks"></a>Comentarios  
 Este método requiere que la interfaz opcional `IRowsetLocate`, que no se admite en todos los proveedores; si éste es el caso, el método devuelve **E_NOINTERFACE**. También debe establecer **DBPROP_IRowsetLocate** a `VARIANT_TRUE` y establecer **DBPROP_CANFETCHBACKWARDS** a `VARIANT_TRUE` antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas.  
  
 Para obtener información sobre el uso de marcadores en los consumidores, consulte [Using Bookmarks](../../data/oledb/using-bookmarks.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [CRowset:: MoveNext](../../data/oledb/crowset-movenext.md)   
 [CRowset:: MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [IRowsetLocate:: GetRowsAt](https://msdn.microsoft.com/en-us/library/ms723031.aspx)   
 [CRowset:: MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)