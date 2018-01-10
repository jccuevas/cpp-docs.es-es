---
title: 'ICommandImpl:: CreateRowset | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ICommandImpl::CreateRowset
- ICommandImpl.CreateRowset
- CreateRowset
dev_langs: C++
helpviewer_keywords: CreateRowset method
ms.assetid: a0890009-205e-4970-879f-01ed9d6a93f1
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4fecb21b35e3941862cc38edc28a2b1e25ff6bcc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="icommandimplcreaterowset"></a>ICommandImpl::CreateRowset
Llamado por el método [Execute](../../data/oledb/icommandimpl-execute.md) para crear un único conjunto de filas.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      template <class   
      RowsetClass  
      >  
HRESULT CreateRowset(  
   IUnknown* pUnkOuter,  
   REFIID riid,  
   DBPARAMS* pParams,  
   DBROWCOUNT* pcRowsAffected,  
   IUnknown** ppRowset,  
   RowsetClass*& pRowsetObj   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `RowsetClass`  
 Un miembro de clase de plantilla que representa la clase de conjunto de filas del usuario. Normalmente, generado por el asistente.  
  
 `pUnkOuter`  
 [in] Un puntero a controlar **IUnknown** interfaz si se está creando el conjunto de filas como parte de un agregado; en caso contrario, es null.  
  
 `riid`  
 [in] Corresponde a `riid` en `ICommand::Execute`.  
  
 `pParams`  
 [los in/out] Corresponde a `pParams` en `ICommand::Execute`.  
  
 `pcRowsAffected`  
 Corresponde a `pcRowsAffected` en `ICommand::Execute`.  
  
 `ppRowset`  
 [los in/out] Corresponde a `ppRowset` en `ICommand::Execute`.  
  
 `pRowsetObj`  
 [out] Un puntero a un objeto de conjunto de filas. Normalmente no se utiliza este parámetro, pero se puede usar si debe realizar más trabajo en el conjunto de filas antes de pasarlo a un objeto COM. La duración de `pRowsetObj` está limitado por `ppRowset`.  
  
## <a name="return-value"></a>Valor devuelto  
 Un valor `HRESULT` estándar. Consulte `ICommand::Execute` para obtener una lista de los valores típicos.  
  
## <a name="remarks"></a>Comentarios  
 Para crear más de un conjunto de filas, o para proporcionar sus propias condiciones para la creación de conjuntos de filas diferentes, realizar llamadas diferentes a `CreateRowset` desde **Execute**.  
  
 Vea [ICommand:: Execute](https://msdn.microsoft.com/en-us/library/ms718095.aspx) en el *referencia del programador OLE DB.*  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [ICommandImpl (Clase)](../../data/oledb/icommandimpl-class.md)