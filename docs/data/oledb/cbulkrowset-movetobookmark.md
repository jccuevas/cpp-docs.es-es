---
title: 'CBulkRowset:: MoveToBookmark | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4b1911fe170262e65ef06e65649f837a0b723d05
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094652"
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