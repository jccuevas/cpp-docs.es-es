---
title: 'CRowset:: CRowset | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowset<TAccessor>::CRowset
- CRowset.CRowset
- ATL::CRowset::CRowset
- ATL::CRowset<TAccessor>::CRowset
- ATL.CRowset.CRowset
- CRowset
- CRowset<TAccessor>.CRowset
- CRowset::CRowset
- ATL.CRowset<TAccessor>.CRowset
dev_langs:
- C++
helpviewer_keywords:
- CRowset class, constructor
ms.assetid: 1c6f72e2-f4f4-48dc-957e-038ae8914ba7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c1ac78caaf82dc42a5e4d4afdab7e03bad53c5f0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098386"
---
# <a name="crowsetcrowset"></a>CRowset::CRowset
Crea un nuevo `CRowset` objeto y (opcionalmente) lo asocia a un [IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx) interfaz proporcionada como un parámetro.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CRowset();   

CRowset(IRowset* pRowset);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pRowset`  
 [in] Un puntero a un `IRowset` interfaz que desee asociar a esta clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CRowset (Clase)](../../data/oledb/crowset-class.md)