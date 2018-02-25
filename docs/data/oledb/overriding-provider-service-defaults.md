---
title: Reemplazar los valores predeterminados de servicio de proveedor | Documentos de Microsoft
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
- service providers [OLE DB]
- OLE DB services [OLE DB], overriding defaults
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8788de8ad28dc3c746155f59dee3ba5bb763bcaa
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="overriding-provider-service-defaults"></a>Reemplazar los valores predeterminados de servicio de un proveedor
El valor del proveedor del registro para **OLEDB_SERVICES** se devuelve como el valor predeterminado para la [DBPROP_INIT_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) propiedad de inicialización en el objeto de origen de datos.  
  
 Siempre que exista la entrada del registro, se agregan los objetos del proveedor y el usuario puede invalidar configuración predeterminada del proveedor en la para servicios habilitados estableciendo el **DBPROP_INIT_OLEDBSERVICES** propiedad antes de la inicialización. Para habilitar o deshabilitar un servicio determinado, el usuario normalmente obtiene el valor actual de la **DBPROP_INIT_OLEDBSERVICES** propiedad, Establece o borra el bit de la propiedad concreta habilitar o deshabilitar y restablece la propiedad. **DBPROP_INIT_OLEDBSERVICES** puede establecerse directamente en OLE DB o en la cadena de conexión pasada a ADO o **IDataInitialize:: GetDatasource**. Los valores correspondientes para habilitar o deshabilitar servicios individuales se muestran en la tabla siguiente.  
  
|Servicios predeterminados habilitados|Valor de la propiedad DBPROP_INIT_OLEDBSERVICES|Valor de cadena de conexión|  
|------------------------------|------------------------------------------------|--------------------------------|  
|Todos los servicios (valor predeterminado)|**DBPROPVAL_OS_ENABLEALL**|"Servicios OLE DB = -1;"|  
|Todas excepto Pooling y AutoEnlistment|**DBPROPVAL_OS_ENABLEALL &**<br /><br /> **~ DBPROPVAL_OS_RESOURCEPOOLING &**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT**|"Servicios OLE DB = de -4;"|  
|Todos los servicios excepto Client Cursor|**DBPROPVAL_OS_ENABLEALL** &<br /><br /> ~**DBPROPVAL_OS_CLIENTCURSOR**|"Servicios OLE DB = -5;"|  
|Todos excepto Pooling, AutoEnlistment y Cursor de cliente|**DBPROPVAL_OS_ENABLEALL &**<br /><br /> **~DBPROPVAL_OS_TXNENLISTMENT &**<br /><br /> **~DBPROPVAL_OS_CLIENTCURSOR**|"Servicios OLE DB = -7;"|  
|No hay servicios|~**DBPROPVAL_OS_ENABLEALL**|"Servicios OLE DB = 0;"|  
  
 Si la entrada del registro no existe para el proveedor, los administradores de componentes, no se agregan los objetos del proveedor y no se invocará ningún servicio, incluso si se solicita explícitamente por el usuario.  
  
## <a name="see-also"></a>Vea también  
 [Agrupación de recursos](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [Cómo utilizan los consumidores la agrupación de recursos](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [Funcionan de proveedores de forma eficaz con la agrupación de recursos](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)