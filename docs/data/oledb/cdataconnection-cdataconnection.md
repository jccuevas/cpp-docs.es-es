---
title: 'CDataConnection:: CDataConnection | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs:
- C++
helpviewer_keywords:
- CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 4405e0dce66de9f006a23b5b680072b9562af06f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Crea e inicializa un `CDataConnection` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
      CDataConnection();   

CDataConnection(const CDataConnection &ds);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ds`  
 [in] Una referencia a una conexión de datos existente.  
  
## <a name="remarks"></a>Comentarios  
 La invalidación de la primera crea un nuevo `CDataConnection` objeto con la configuración predeterminada.  
  
 El segundo reemplazada crea un nuevo `CDataConnection` objeto con una configuración equivalente para el objeto de conexión de datos que especificó.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [CDataConnection (Clase)](../../data/oledb/cdataconnection-class.md)