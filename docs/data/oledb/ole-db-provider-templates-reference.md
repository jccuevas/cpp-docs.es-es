---
title: "Referencia de plantillas de proveedores OLE DB | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.templates.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "plantillas del proveedor OLE DB"
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Referencia de plantillas de proveedores OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las clases e interfaces para las plantillas de proveedor OLE DB se pueden agrupar en las categorías siguientes.  El material de referencia también incluye información sobre [macros para las plantillas de proveedor OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Las clases utilizan la convención de nomenclatura siguiente: una clase denominada con el modelo **IWidgetImpl** proporcionaría una implementación de la interfaz **IWidget**.  
  
## Clases de sesión  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Crea una nueva sesión del objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada.  Interfaz de enlace en objetos de origen de datos.  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implementar propiedades de sesión llamando a una función estática definida por el mapa del conjunto de propiedades.  El mapa del conjunto de propiedades se debe especificar en la clase de sesión.  Interfaz de enlace en sesiones.  
  
## Clases de conjuntos de filas  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 Proporciona una implementación de conjunto de filas OLE DB sin requerir la herencia múltiple de las interfaces de implementación.  El único método para el que debe proporcionar la implementación es **Ejecución**.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en la clase de `IRowsetImpl` .  Un identificador de fila es lógicamente etiqueta única para una fila de resultados.  `IRowsetImpl` crea nuevo `CSimpleRow` para cada fila solicitada en `IRowsetImpl::GetNextRows`.  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB requiere los proveedores implementar **HACCESSOR**, que es una etiqueta a una matriz de estructuras de **DBBINDING** .  Proporciona s para **HACCESSOR**que es direcciones de estructuras de **BindType** .  Obligatorio en conjuntos de filas y los comandos.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Delegados a una función estática definida por el mapa de columnas del proveedor.  Interfaz de enlace en conjuntos de filas y los comandos.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Proporciona información sobre la disponibilidad de conversiones de tipos en un comando o en un conjunto de filas.  Obligatorio en comandos, conjuntos de filas, y conjuntos de filas de índice.  Implementa la interfaz de **IConvertType** delegando a la conversión del objeto proporcionado por OLE DB.  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implementa la interfaz y la función templatized `CreateSchemaRowset`de **IDBSchemaRowset** de generador.  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 Abre y devuelve un conjunto de filas que incluya todas las filas de una sola tabla o índice.  Interfaz de enlace para un objeto de sesión.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implementa la interfaz OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) , que permite actualizar de los valores de las columnas en las filas existentes, eliminando filas, e insertar nuevas filas.  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 Esta clase hereda de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) y reemplaza [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869).  `IRowsetCreatorImpl` realiza las mismas funciones que `IObjectWithSite` pero también habilita las propiedades **DBPROPCANSCROLLBACKWARDS** y **DBPROPCANFETCHBACKWARDS**OLE DB.  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 Implementa la interfaz de **IRowsetIdentity** , que permite comparar si dos filas de datos sean idénticas o no.  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 Proporciona una implementación de la interfaz de `IRowset` , que es la interfaz base de conjunto de filas.  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 Implementa las propiedades del conjunto de filas utilizando el mapa del conjunto de propiedades definido en la clase de comando.  Interfaz de enlace en conjuntos de filas.  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 Implementa la interfaz OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) , que captura filas arbitrarias de un conjunto de filas.  Para admitir los marcadores de OLE DB en un conjunto de filas, haga que el conjunto de filas heredan de esta clase.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implementa funciones de difusión para advertir a los agentes de escucha del punto de conexión **IID\_IRowsetNotify** de cambios en el contenido del conjunto de filas.  Los consumidores que controlan notificaciones implementan [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) y se registran en ese punto de conexión.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implementa la interfaz OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) , que permite a los consumidores para retrasar la transmisión de los cambios realizados con [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) al origen de datos y deshacer cambia antes de la transmisión.  
  
## Clases de comando  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 Proporciona una implementación de la interfaz `ICommand`.  Esta interfaz no está visible, pero es administrada por **ICommandTextImpl**.  Una interfaz de enlace en el objeto de comando.  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 Esta implementación de la interfaz de **ICommandProperties** proporciona una función estática definida por la macro de `BEGIN_PROPSET_MAP` .  Obligatorio de comandos.  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 Los conjuntos, almacenan, y devuelve el texto del comando.  Obligatorio de comandos.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Crea un nuevo comando del objeto de sesión y devuelve la interfaz solicitada en el comando creado recientemente.  Interfaz opcional en objetos de sesión.  
  
 Otras clases de comando son `IColumnsInfoImpl` y `IAccessorImpl`, descritos en la sección de las clases de conjunto de filas anteriormente.  
  
## Clases de origen de datos  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 Crea y elimina la conexión con el consumidor.  Interfaz de enlace en objetos de origen de datos y interfaz opcional de enumeradores.  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` es una interfaz de enlace para los objetos de origen de datos y una interfaz opcional para los enumeradores.  Sin embargo, si un enumerador expone **IDBInitialize**, debe exponer `IDBProperties` \(propiedades del origen de datos\).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Obtiene un puntero de interfaz al objeto de origen de datos.  Interfaz de enlace en la sesión.  
  
## Otras clases  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 Implementa las propiedades de una variedad de interfaces de propiedades OLE DB \(por ejemplo, `IDBProperties`, **ISessionProperties**, y `IRowsetInfo`\).  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implementa la interfaz OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) , agregando registros a y recuperar los registros de un miembro de datos.  
  
## Vea también  
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [plantillas OLE DB](../../data/oledb/ole-db-templates.md)