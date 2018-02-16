---
title: 'CDynamicAccessor:: CDynamicAccessor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDynamicAccessor::CDynamicAccessor
- ATL::CDynamicAccessor::CDynamicAccessor
- ATL.CDynamicAccessor.CDynamicAccessor
- CDynamicAccessor.CDynamicAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicAccessor class, constructor
ms.assetid: bf40fe81-2c85-473e-9075-51ad9b060b39
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ce33fd4aa64114a0b4465bb3272f74ef2ccf8258
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="cdynamicaccessorcdynamicaccessor"></a>CDynamicAccessor::CDynamicAccessor
Crea e inicializa la `CDynamicAccessor` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CDynamicAccessor(DBBLOBHANDLINGENUM eBlobHandling = DBBLOBHANDLING_DEFAULT,   
   DBLENGTH nBlobSize = 8000);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `eBlobHandling`  
 Especifica cómo se controlan los datos de objeto binario grande (BLOB). El valor predeterminado es **DBBLOBHANDLING_DEFAULT**. Vea [SetBlobHandling](../../data/oledb/cdynamicaccessor-setblobhandling.md) para obtener una descripción de la **DBBLOBHANDLINGENUM** valores.  
  
 `nBlobSize`  
 El tamaño máximo de BLOB en bytes; datos de la columna sobre este valor se tratan como un BLOB. El valor predeterminado es 8000. Vea [SetBlobSizeLimit](../../data/oledb/cdynamicaccessor-setblobsizelimit.md) para obtener más información.  
  
## <a name="remarks"></a>Comentarios  
 Si se utiliza el constructor para inicializar el `CDynamicAccessor` de objetos, puede especificar cómo se enlazará BLOBs. BLOBs pueden contener datos binarios como gráficos, sonido o compilado el código. El comportamiento predeterminado es tratar las columnas más de 8.000 bytes como BLOBs e intentar enlazarlos a un `ISequentialStream` objeto. Sin embargo, puede especificar un valor diferente para que sea el tamaño del BLOB.  
  
 También puede especificar cómo `CDynamicAccessor` administra los datos de columna que se consideran datos BLOB: puede controlar los datos de BLOB de la manera predeterminada; puede omitir (no enlazar) datos BLOB; o se puede enlazar datos BLOB de memoria asignada por el proveedor.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)