---
title: 'CAccessorBase:: Gethaccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetHAccessor
- CAccessorBase::GetHAccessor
- CAccessorBase.GetHAccessor
dev_langs: C++
helpviewer_keywords: GetHAccessor method
ms.assetid: 1bb98762-0752-4aae-a0b6-ba96bec03621
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ba60cb6dd108b0ea451baabf5941caeead11a42f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="caccessorbasegethaccessor"></a>CAccessorBase::GetHAccessor
Recupera el identificador de descriptor de acceso de un descriptor de acceso especificado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      HACCESSOR GetHAccessor(  
   ULONG nAccessor   
) const;  
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