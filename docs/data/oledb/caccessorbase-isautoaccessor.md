---
title: 'CAccessorBase:: Isautoaccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IsAutoAccessor
- CAccessorBase.IsAutoAccessor
- CAccessorBase::IsAutoAccessor
dev_langs: C++
helpviewer_keywords: IsAutoAccessor method
ms.assetid: c330da15-2947-4050-ad00-8f776adc58fb
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a08251ddf32f815390c28677f03536e1c2cec7d9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="caccessorbaseisautoaccessor"></a>CAccessorBase::IsAutoAccessor
Devuelve true si los datos se recuperan automáticamente para el descriptor de acceso durante una operación de movimiento.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      bool IsAutoAccessor(  
   ULONG nAccessor   
) const;  
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