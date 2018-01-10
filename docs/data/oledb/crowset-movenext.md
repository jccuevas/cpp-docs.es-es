---
title: 'CRowset:: MoveNext | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL.CRowset<TAccessor>.MoveNext
- ATL.CRowset.MoveNext
- ATL::CRowset<TAccessor>::MoveNext
- CRowset<TAccessor>.MoveNext
- CRowset.MoveNext
- CRowset<TAccessor>::MoveNext
- CRowset::MoveNext
- ATL::CRowset::MoveNext
dev_langs: C++
helpviewer_keywords: MoveNext method
ms.assetid: 0df3288c-2bce-494f-99c0-6344b54a4adf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: bd997b25125a48dd6103629e6957843295532901
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crowsetmovenext"></a>CRowset::MoveNext
Mueve el cursor hasta el siguiente registro.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HRESULT MoveNext( ) throw( );   
HRESULT MoveNext(   
   LONG lSkip,   
   bool bForward = true    
) throw( );  
```  
  
#### <a name="parameters"></a>Parámetros  
 `lSkip`  
 [in] El número de filas que se omiten antes de capturar.  
  
 `bForward`  
 [in] Pasar **true** para desplazarse hacia delante hasta el siguiente registro **false** para moverse hacia atrás.  
  
## <a name="return-value"></a>Valor devuelto  
 Un `HRESULT` estándar. Cuando se ha alcanzado el final del conjunto de filas, devuelve **DB_S_ENDOFROWSET**.  
  
## <a name="remarks"></a>Comentarios  
 Recopila la siguiente fila secuencial desde el `CRowset` objeto, teniendo en cuenta la posición anterior. Si lo desea, puede saltarse lecciones `lSkip` filas o desplazarse hacia atrás.  
  
 Este método requiere que establezca las propiedades siguientes antes de llamar a **abiertos** en la tabla o el comando que contiene el conjunto de filas:  
  
-   **DBPROP_CANSCROLLBACKWARDS** debe ser `VARIANT_TRUE` si `lSkip` < 0  
  
-   **DBPROP_CANFETCHBACKWARDS** debe ser `VARIANT_TRUE` si `bForward` = false  
  
 En caso contrario (si `lSkip` > = 0 y `bForward` = true), no es necesario establecer las propiedades adicionales.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (clase)](../../data/oledb/crowset-class.md)   
 [CRowset:: MoveFirst](../../data/oledb/crowset-movefirst.md)   
 [CRowset:: MoveToBookmark](../../data/oledb/crowset-movetobookmark.md)   
 [CRowset:: MovePrev](../../data/oledb/crowset-moveprev.md)   
 [CRowset::MoveLast](../../data/oledb/crowset-movelast.md)