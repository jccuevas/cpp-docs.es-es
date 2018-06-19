---
title: 'CDynamicParameterAccessor:: CDynamicParameterAccessor | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::CDynamicParameterAccessor
- CDynamicParameterAccessor.CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class, constructor
- CDynamicParameterAccessor method
ms.assetid: a1cce5e4-dfb9-43a2-bfb8-0435c653674a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 52ffd2f16211ae25bf1069ad1860dc273c1d5002
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098399"
---
# <a name="cdynamicparameteraccessorcdynamicparameteraccessor"></a>CDynamicParameterAccessor::CDynamicParameterAccessor
El constructor.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      typedef CDynamicParameterAccessor _ParamClass;  
CDynamicParameterAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000 )   
   : CDynamicAccessor(eBlobHandling, nBlobSize )  
```  
  
#### <a name="parameters"></a>Parámetros  
 `eBlobHandling`  
 Especifica cómo se controlan los datos de BLOB. El valor predeterminado es **DBBLOBHANDLING_DEFAULT**. Vea [CDynamicAccessor:: Setblobhandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de la **DBBLOBHANDLINGENUM** valores.  
  
 `nBlobSize`  
 El tamaño máximo de BLOB en bytes; datos de la columna sobre este valor se tratan como un BLOB. El valor predeterminado es 8000. Vea [CDynamicAccessor:: Setblobsizelimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.  
  
## <a name="remarks"></a>Comentarios  
 Consulte la [CDynamicAccessor:: CDynamicAccessor](../../data/oledb/cdynamicaccessor-cdynamicaccessor.md) constructor para obtener más información sobre el control de BLOB.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)