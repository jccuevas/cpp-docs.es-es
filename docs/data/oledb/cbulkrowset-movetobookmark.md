---
title: CBulkRowset::MoveToBookmark | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CBulkRowset<TAccessor>::MoveToBookmark
- CBulkRowset.MoveToBookmark
- MoveToBookmark
- ATL.CBulkRowset.MoveToBookmark
- CBulkRowset::MoveToBookmark
- ATL::CBulkRowset<TAccessor>::MoveToBookmark
- ATL::CBulkRowset::MoveToBookmark
dev_langs:
- C++
helpviewer_keywords:
- MoveToBookmark method
ms.assetid: 76aab025-819e-4ecd-ae0a-d8d3fb2d2099
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 07703acbe483f30c2d458f481b7ff301c937d6d4
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cbulkrowsetmovetobookmark"></a>CBulkRowset::MoveToBookmark
Recopila la fila marcada por fila en un desplazamiento especificado o un marcador (`lSkip`) de ese marcador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT MoveToBookmark(const CBookmarkBase& bookmark,  
   DBCOUNTITEM lSkip = 0) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 `bookmark`  
 [in] Un marcador marcar la ubicación desde la que va a capturar datos.  
  
 `lSkip`  
 [in] El recuento de número de filas de marcador a la fila de destino. Si `lSkip` es cero, la primera fila es la fila marcada. Si `lSkip` es 1, la primera fila es la fila después de la fila marcada. Si `lSkip` es -1, la primera fila es la fila antes de la fila marcada.  
  
## <a name="return-value"></a>Valor devuelto  
 Vea [IRowset:: GetData](https://msdn.microsoft.com/en-us/library/ms716988.aspx) en el *referencia del programador OLE DB*.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CBulkRowset (Clase)](../../data/oledb/cbulkrowset-class.md)