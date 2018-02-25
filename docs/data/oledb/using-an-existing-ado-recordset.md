---
title: Con un conjunto de registros ADO existente | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ADO recordsets [C++]
- OLE DB consumer templates, ADO recordsets
- recordsets [C++], using in OLE DB
ms.assetid: a9b1de8a-d379-49b1-a26e-578741e9f6a8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a819a0f292951060f4dc6b9fdda580db8f0d2127
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="using-an-existing-ado-recordset"></a>Utilizar un conjunto de registros ADO existente
Para mezclar las plantillas de consumidor OLE DB y Active Data Objects (ADO), use ADO para abrir un conjunto de registros (correspondiente a un conjunto de filas en las plantillas de consumidor OLE DB). Cuando tenga un conjunto de registros, haga lo siguiente para conectarse a un conjunto de filas de OLE DB:  
  
1.  Llame a `QueryInterface` para el `IRowset` y `IAccessor` punteros.  
  
    ```  
    IRowset* lpRowset = NULL;  
    IAccessor* lpAccessor = NULL;  
    lpUnk->QueryInterface(IID_IRowset, (void**)&lpRowset);  
    lpUnk->QueryInterface(IID_IAccessor, (void**)&lpAccessor);  
    ```  
  
    > [!NOTE]
    >  *lpUnk* apunta a la **IUnknown** objeto del conjunto de registros ADO.  
  
2.  Asociar el descriptor de acceso y el conjunto de filas a sus clases de plantillas de consumidor OLE DB adecuados.  
  
    ```  
    CRowset rs;  
    CAccessor accessor;  
  
    accessor.AddAccessorInfo(0ul);      // 0 is the ordinal of an ADO accessor  
    rs.m_spRowset.Attach(lpRowset);      // use the Attach method of CComPtr<>  
    rs.SetAccessor(accessor);  
    ```  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)