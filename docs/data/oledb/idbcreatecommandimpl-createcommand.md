---
title: 'Idbcreatecommandimpl:: CreateCommand | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDBCreateCommandImpl.CreateCommand
- CreateCommand
- IDBCreateCommandImpl::CreateCommand
dev_langs:
- C++
helpviewer_keywords:
- CreateCommand method
ms.assetid: 50ffbf8b-2c07-4bcb-96c5-ffce4519c7f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 38b9c3963c3e491412de85e7c4f72f2e4525c406
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
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