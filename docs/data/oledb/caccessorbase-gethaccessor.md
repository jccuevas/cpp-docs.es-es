---
title: 'CAccessorBase:: Gethaccessor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
dev_langs:
- C++
helpviewer_keywords:
- GetHAccessor method
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2bacc7f24d112fc6714200c6347e66bb66866831
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorbasegethaccessor"></a>CAccessorBase::GetHAccessor
Recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      HACCESSOR GetHAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nAccessor`  
 [in] El número de desplazamiento cero para el descriptor de acceso.  
  
## <a name="return-value"></a>Valor devuelto  
 El identificador de descriptor de acceso.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CAccessorBase (Clase)](../../data/oledb/caccessorbase-class.md)