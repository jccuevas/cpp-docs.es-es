---
title: 'Idbcreatecommandimpl:: CreateCommand | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 709f734ad0349ea7908466958e282a8ca2a5c2db
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101619"
---
# <a name="idbcreatecommandimplcreatecommand"></a>IDBCreateCommandImpl::CreateCommand
Crea un nuevo comando y devuelve la interfaz solicitada.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(CreateCommand)(IUnknown * pUnkOuter,   
   REFIID riid,   
   IUnknown ** ppvCommand);  
```  
  
#### <a name="parameters"></a>Parámetros  
 Vea [IDBCreateCommand:: CreateCommand](https://msdn.microsoft.com/en-us/library/ms709772.aspx) en el *referencia del programador OLE DB*.  
  
 Algunos parámetros corresponden a *referencia del programador de OLE DB* parámetros de nombres diferentes, que se describen en **IDBCreateCommand:: CreateCommand**:  
  
|Parámetros de plantilla OLE DB|*Referencia del programador de OLE DB* parámetros|  
|--------------------------------|------------------------------------------------|  
|*ppvCommand*|*ppCommand*|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="see-also"></a>Vea también  
 [IDBCreateCommandImpl (Clase)](../../data/oledb/idbcreatecommandimpl-class.md)