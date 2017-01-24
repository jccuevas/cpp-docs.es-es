---
title: "Reemplazar los valores predeterminados de servicio de un proveedor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "servicios OLE DB [OLE DB], reemplazar valores predeterminados"
  - "proveedores de servicios [OLE DB]"
ms.assetid: 08e366c0-74d8-463b-93a6-d58a8dc195f8
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reemplazar los valores predeterminados de servicio de un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El valor del Registro del proveedor para **OLEDB\_SERVICES** se devuelve como valor predeterminado para la propiedad de inicialización [DBPROP\_INIT\_OLEDBSERVICES](https://msdn.microsoft.com/en-us/library/ms716898.aspx) sobre el objeto de origen de datos.  
  
 Con tal de que exista la entrada del Registro, se agregan los objetos del proveedor y el usuario puede reemplazar el valor predeterminado del proveedor para servicios habilitados estableciendo el valor de la propiedad **DBPROP\_INIT\_OLEDBSERVICES** antes de la inicialización.  Para habilitar o deshabilitar un servicio determinado, generalmente el usuario obtiene el valor actual de la propiedad **DBPROP\_INIT\_OLEDBSERVICES**, establece o desactiva el bit de la propiedad concreta como habilitada o deshabilitada, y restablece el valor de la propiedad.  Se puede establecer directamente el valor de **DBPROP\_INIT\_OLEDBSERVICES** en OLE DB o en la cadena de conexión pasada a ADO o **IDataInitialize::GetDatasource**.  Los valores correspondientes para habilitar o deshabilitar servicios individuales se muestran en la tabla siguiente.  
  
|Servicios predeterminados habilitados|Valor de propiedad DBPROP\_INIT\_OLEDBSERVIC|Valor de la cadena de conexión|  
|-------------------------------------------|--------------------------------------------------|------------------------------------|  
|Todos los servicios \(predeterminado\)|**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= \-1;"|  
|Todos los servicios excepto Pooling y AutoEnlistment|**DBPROPVAL\_OS\_ENABLEALL &**<br /><br /> **~DBPROPVAL\_OS\_RESOURCEPOOLING &**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT**|"OLE DB Services \= \-4;"|  
|Todos los servicios excepto Client Cursor|**DBPROPVAL\_OS\_ENABLEALL** &<br /><br /> ~**DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-5;"|  
|Todos los servicios, excepto Pooling, AutoEnlistment y Client Cursor|**DBPROPVAL\_OS\_ENABLEALL &**<br /><br /> **~DBPROPVAL\_OS\_TXNENLISTMENT &**<br /><br /> **~DBPROPVAL\_OS\_CLIENTCURSOR**|"OLE DB Services \= \-7;"|  
|Ningún servicio|~**DBPROPVAL\_OS\_ENABLEALL**|"OLE DB Services \= 0;"|  
  
 Si no existe ninguna entrada del Registro para el proveedor, los Administradores de componentes no agregarán los objetos del proveedor y no se invocará ningún servicio, aunque lo solicite explícitamente el usuario.  
  
## Vea también  
 [Resource Pooling](https://msdn.microsoft.com/en-us/library/ms713655.aspx)   
 [How Consumers Use Resource Pooling](https://msdn.microsoft.com/en-us/library/ms715907.aspx)   
 [How Providers Work Effectively with Resource Pooling](https://msdn.microsoft.com/en-us/library/ms714906.aspx)   
 [Habilitar y deshabilitar servicios OLE DB](../../data/oledb/enabling-and-disabling-ole-db-services.md)