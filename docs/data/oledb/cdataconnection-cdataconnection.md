---
title: 'CDataConnection:: CDataConnection | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
dev_langs: C++
helpviewer_keywords: CDataConnection class, constructor
ms.assetid: ac25c9a0-44d3-4083-b13f-76c07772e12d
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e92019f3f49257e297bddb2f717cf416da62a3bc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cdataconnectioncdataconnection"></a>CDataConnection::CDataConnection
Crea e inicializa un `CDataConnection` objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
  
      CDataConnection();   
CDataConnection(  
   const CDataConnection &ds  
);  
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