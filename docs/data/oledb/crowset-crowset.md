---
title: CRowset::CRowset | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1038ff5de27dd7ba17c48fc2a4159cb33d56022c
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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