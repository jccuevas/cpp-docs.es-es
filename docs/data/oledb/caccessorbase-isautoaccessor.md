---
title: 'CAccessorBase:: Isautoaccessor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs:
- C++
helpviewer_keywords:
- IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: fabf5d182b6fb0eb993300e241ae76e1b61f5cef
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="caccessorbaseisautoaccessor"></a>CAccessorBase::IsAutoAccessor
Devuelve true si los datos se recuperan automáticamente para el descriptor de acceso durante una operación de movimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      bool IsAutoAccessor(ULONG nAccessor) const;  
```  
  
#### <a name="parameters"></a>Parámetros  
 `nAccessor`  
 [in] El número de desplazamiento cero para el descriptor de acceso.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve **true** si el descriptor de acceso es autoaccessor. En caso contrario, devuelve **false**.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CAccessorBase (Clase)](../../data/oledb/caccessorbase-class.md)