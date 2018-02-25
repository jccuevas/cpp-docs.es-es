---
title: Referencia de plantillas del proveedor OLE DB | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.templates.ole
dev_langs:
- C++
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 68c741f09772c881b42dc4e4cd17de31ed107f8c
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="ole-db-provider-templates-reference"></a>Referencia de plantillas de proveedores OLE DB
Las clases e interfaces para las plantillas de proveedor OLE DB pueden agruparse en las siguientes categorías. El material de referencia también incluye información sobre la [macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).  
  
 Las clases utilizan la convención de nomenclatura siguiente: una clase denominada con el patrón **IWidgetImpl** podría proporcionar una implementación de la interfaz **IWidget**.  
  
## <a name="session-classes"></a>Clases de sesión  
 [IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)  
 Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada. Interfaz obligatoria en los objetos de origen de datos.  
  
 [ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)  
 Implementa las propiedades de la sesión mediante una llamada a una función estática definida en la asignación de conjunto de propiedades. La asignación de conjunto de propiedad debe especificarse en la clase de sesión. Interfaz obligatoria en las sesiones.  
  
## <a name="rowset-classes"></a>Clases de conjunto de filas  
 [CRowsetImpl](../../data/oledb/crowsetimpl-class.md)  
  
 Proporciona una implementación de conjunto de filas de OLE DB estándar sin necesidad de herencia múltiple de las interfaces de implementación. El único método para el que debe proporcionar la implementación es **Execute**.  
  
 [CSimpleRow](../../data/oledb/csimplerow-class.md)  
 Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en la `IRowsetImpl` clase. Un identificador de fila es, lógicamente, una etiqueta única para una fila de resultados. `IRowsetImpl` crea un nuevo `CSimpleRow` para todas las filas solicitaron en `IRowsetImpl::GetNextRows`.  
  
 [IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)  
 OLE DB requiere que los proveedores implementar un **HACCESSOR**, que es una etiqueta a una matriz de **DBBINDING** estructuras. Proporciona **HACCESSOR**s que son direcciones de la **BindType** estructuras. Obligatoria en los conjuntos de filas y comandos.  
  
 [IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)  
 Delegados a una función estática definida en la asignación de columna de proveedor. Interfaz obligatoria en conjuntos de filas y comandos.  
  
 [IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)  
 Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas. Obligatoria en los conjuntos de filas de índice, comandos y conjuntos de filas. Implementa el **IConvertType** interfaz mediante la delegación para el objeto de conversión proporcionado por OLE DB.  
  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)  
 Implementa el **IDBSchemaRowset** interfaz y la función de creador de plantillas `CreateSchemaRowset`.  
  
 [IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)  
 Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice. Interfaz obligatoria para un objeto de sesión.  
  
 [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)  
 Implementa OLE DB [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) interfaz, lo que permite la actualización de los valores de columnas en las filas existentes, eliminar filas e insertar nuevas filas.  
  
 [IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)  
 Esta clase hereda de [IObjectWithSite](http://msdn.microsoft.com/library/windows/desktop/ms693765) e invalida [IObjectWithSite::SetSite](http://msdn.microsoft.com/library/windows/desktop/ms683869). `IRowsetCreatorImpl` realiza las mismas funciones que `IObjectWithSite` , pero también permite que las propiedades de OLE DB **DBPROPCANSCROLLBACKWARDS** y **DBPROPCANFETCHBACKWARDS**.  
  
 [IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)  
 Implementa el **IRowsetIdentity** interfaz, que le permite comparar si dos filas de datos son idénticos o no.  
  
 [IRowsetImpl](../../data/oledb/irowsetimpl-class.md)  
 Proporciona una implementación de la `IRowset` interfaz, que es la interfaz de conjunto de filas base.  
  
 [IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)  
 Implementa las propiedades del conjunto de filas mediante la propiedad de asignación definida en la clase de comando Set. Interfaz obligatoria en conjuntos de filas.  
  
 [IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)  
 Implementa OLE DB [IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx) interfaz, que captura filas arbitrarias desde un conjunto de filas. Para admitir marcadores de OLE DB en un conjunto de filas, haga que el conjunto de filas herede de esta clase.  
  
 [IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)  
 Implementa las funciones para informar de los agentes de escucha en el punto de conexión de difusión **IID_IRowsetNotify** de los cambios en el contenido del conjunto de filas. Los consumidores que administrar notificaciones implementan [IRowsetNotify](https://msdn.microsoft.com/en-us/library/ms712959.aspx) y regístrelo en ese punto de conexión.  
  
 [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)  
 Implementa OLE DB [IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx) interfaz, que permite a los consumidores retrasar la transmisión de los cambios realizados con [IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx) al origen de datos y deshacer los cambios antes de la transmisión.  
  
## <a name="command-classes"></a>Clases de comandos  
 [ICommandImpl](../../data/oledb/icommandimpl-class.md)  
 Proporciona una implementación de la `ICommand` interfaz. Esta interfaz no está visible, pero se controla mediante **ICommandTextImpl**. Una interfaz obligatoria en el objeto de comando.  
  
 [ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)  
 Esta implementación de la **ICommandProperties** interfaz proporciona una función estática definida por el `BEGIN_PROPSET_MAP` macro. Obligatoria en los comandos.  
  
 [ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)  
 Establece, almacena y devuelve el texto del comando. Obligatoria en los comandos.  
  
 [IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)  
 Crea un nuevo comando desde el objeto de sesión y devuelve la interfaz solicitada en el comando recién creado. Interfaz opcional en objetos de sesión.  
  
 Otras clases de comando son `IColumnsInfoImpl` y `IAccessorImpl`, que se describen en la sección de las clases de conjunto de filas anterior.  
  
## <a name="data-source-classes"></a>Clases de origen de datos  
 [IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)  
 Crea y elimina la conexión con el consumidor. Interfaz obligatoria en los objetos de origen de datos y la interfaz opcional sobre los enumeradores.  
  
 [IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)  
 `IDBProperties` es una interfaz obligatoria para los objetos de origen de datos y una interfaz opcional para los enumeradores. Sin embargo, si expone un enumerador **IDBInitialize**, debe exponer `IDBProperties` (propiedades del origen de datos).  
  
 [IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)  
 Obtiene un puntero de interfaz al objeto de origen de datos. Interfaz obligatoria en la sesión.  
  
## <a name="other-classes"></a>Otras clases  
 [CUtlProps](../../data/oledb/cutlprops-class.md)  
 Implementa las propiedades para una variedad de interfaces de la propiedad de OLE DB (por ejemplo, `IDBProperties`, **ISessionProperties**, y `IRowsetInfo`).  
  
 [IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)  
  
 Implementa OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfaz, agregar registros a y recuperar los registros de un miembro de datos.  
  
## <a name="see-also"></a>Vea también  
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [Plantillas OLE DB](../../data/oledb/ole-db-templates.md)