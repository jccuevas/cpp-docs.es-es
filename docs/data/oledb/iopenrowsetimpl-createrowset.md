---
title: 'Iopenrowsetimpl:: CreateRowset | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOpenRowsetImpl.CreateRowset
- IOpenRowsetImpl::CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: 69041cf6-7a2f-4409-a26e-6e984c24986e
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: ada7e23a3ff48ea9b97263c8fa94a7970185f7a5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="iopenrowsetimplcreaterowset"></a>IOpenRowsetImpl::CreateRowset
Crea un objeto de conjunto de filas. No llama directamente al usuario. Vea [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en el *referencia del programador OLE DB.*  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   DBID* pTableID,  
   DBID* pIndexID,  
   REFIID riid,  
   ULONG cPropertySets,  
   DBPROPSET rgPropertySets[],  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `RowsetClass`  
 Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente, generado por el asistente.  
  
 `pRowsetObj`  
 [out] Un puntero a un objeto de conjunto de filas. Normalmente no se utiliza este parámetro, pero se puede usar si debe realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de `pRowsetObj` está limitado por `ppRowset`.  
  
 Para otros parámetros, vea [IOpenRowset:: OpenRowset](https://msdn.microsoft.com/en-us/library/ms716724.aspx) en el *referencia del programador de OLE DB.*  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IOpenRowsetImpl (Clase)](../../data/oledb/iopenrowsetimpl-class.md)