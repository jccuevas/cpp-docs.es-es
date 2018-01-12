---
title: CDataConnection (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
dev_langs: C++
helpviewer_keywords: CDataConnection class
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 65e147366ecb7120a9dd2a98cde0c812d02582da
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cdataconnection-class"></a>CDataConnection (Clase)
Administra la conexión con el origen de datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class CDataConnection  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[CDataConnection](../../data/oledb/cdataconnection-cdataconnection.md)|Constructor. Crea e inicializa un `CDataConnection` objeto.|  
|[Copiar](../../data/oledb/cdataconnection-copy.md)|Crea una copia de una conexión de datos existente.|  
|[Abrir](../../data/oledb/cdataconnection-open.md)|Abre una conexión a un origen de datos utilizando una cadena de inicialización.|  
|[OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md)|Abre una nueva sesión en la conexión actual.|  
  
### <a name="operators"></a>Operadores  
  
|||  
|-|-|  
|[operador BOOL](../../data/oledb/cdataconnection-operator-bool.md)|Determina si la sesión actual está abierta o no.|  
|[operator bool](../../data/oledb/cdataconnection-operator-bool-ole-db.md)|Determina si la sesión actual está abierta o no.|  
|[operador CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md)|Devuelve una referencia al contenido `CDataSource` objeto.|  
|[operador CDataSource *](../../data/oledb/cdataconnection-operator-cdatasource-star.md)|Devuelve un puntero para el objeto contenido `CDataSource` objeto.|  
|[operador CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md)|Devuelve una referencia al contenido `CSession` objeto.|  
|[operador CSession *](../../data/oledb/cdataconnection-operator-csession-star.md)|Devuelve un puntero para el objeto contenido `CSession` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 `CDataConnection`clase es útil para crear clientes porque encapsula los objetos necesarios (origen de datos y sesión) y algunas de las tareas que se debe hacer cuando se conecta a un origen de datos  
  
 Sin `CDataConnection`, tiene que crear un `CDataSource` objeto, llame a su [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) método, a continuación, cree una instancia de un [CSession](../../data/oledb/csession-class.md) objeto, llame a su [ Abrir](../../data/oledb/csession-open.md) método, a continuación, cree un [CCommand](../../data/oledb/ccommand-class.md) objeto y llame al método su **abiertos*** métodos.  
  
 Con `CDataConnection`, basta con crear un objeto de conexión, pase una cadena de inicialización y luego use esa conexión para comandos de apertura. Si planea usar la conexión a la base de datos varias veces, resulta una buena idea para mantener la conexión abierta, y `CDataConnection` proporciona una manera cómoda de hacerlo.  
  
> [!NOTE]
>  Si va a crear una aplicación de base de datos que necesita para administrar varias sesiones, necesitará usar [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)