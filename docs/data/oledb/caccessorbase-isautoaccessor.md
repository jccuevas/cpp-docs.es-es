---
title: 'CAccessorBase:: Isautoaccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs:
- C++
helpviewer_keywords:
- IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 168956019b419f80e8d630e58960b9ba2d07a761
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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