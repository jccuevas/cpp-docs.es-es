---
title: Reemplazar los valores predeterminados de servicio de proveedor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 106d1991f5312065aa78330888e55383d1f9506a
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337023"
---
# <a name="overriding-provider-service-defaults"></a>Reemplazar los valores predeterminados de servicio de un proveedor
Se devuelve el valor del proveedor del registro para OLEDB_SERVICES como el valor predeterminado para el [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/library/ms716898.aspx) propiedad de inicialización en el objeto de origen de datos.  
  
 Siempre y cuando la entrada del registro existe, se agregan los objetos del proveedor y el usuario puede invalidar valor predeterminado del proveedor para los servicios habilitados estableciendo el `DBPROP_INIT_OLEDBSERVICES` propiedad antes de la inicialización. Para habilitar o deshabilitar un servicio determinado, el usuario normalmente obtiene el valor actual de la `DBPROP_INIT_OLEDBSERVICES` propiedad, Establece o borra el bit habilitar o deshabilitar la propiedad determinada y restablece la propiedad. `DBPROP_INIT_OLEDBSERVICES` se puede establecer directamente en OLE DB o en la cadena de conexión pasada a ADO o `IDataInitialize::GetDatasource`. Los valores correspondientes para habilitar o deshabilitar servicios individuales se muestran en la tabla siguiente.  
  
|Servicios predeterminados habilitados|Valor de la propiedad DBPROP_INIT_OLEDBSERVICES|Valor de cadena de conexión|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Todos los servicios (valor predeterminado)|`DBPROPVAL_OS_ENABLEALL`|"Servicios OLE DB = -1;"|  
|Todos excepto la agrupación y AutoEnlistment|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_RESOURCEPOOLING &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT`|"Servicios OLE DB = -4;"|  
|Todos excepto el Cursor de cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios OLE DB = -5;"|  
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|`DBPROPVAL_OS_ENABLEALL &`<br /><br /> `~DBPROPVAL_OS_TXNENLISTMENT &`<br /><br /> `~DBPROPVAL_OS_CLIENTCURSOR`|"Servicios OLE DB = -7;"|  
|No hay servicios|`~DBPROPVAL_OS_ENABLEALL`|"Servicios OLE DB = 0;"|  
  
 Si la entrada del registro no existe para el proveedor, los administradores de componentes, no se agregan los objetos del proveedor y no se invocará ningún servicio, incluso si se solicita explícitamente por el usuario.  
  
## <a name="see-also"></a>Vea también  
 [Agrupación de recursos](https://msdn.microsoft.com/library/ms713655.aspx)   
 [Cómo los consumidores utilizan la agrupación de recursos](https://msdn.microsoft.com/library/ms715907.aspx)   
 [Funcionan de proveedores de forma eficaz con la agrupación de recursos](https://msdn.microsoft.com/library/ms714906.aspx)   
 [Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)