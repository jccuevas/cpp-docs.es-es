---
title: Referencia de plantillas de proveedores OLE DB
ms.date: 11/04/2016
f1_keywords:
- vc.templates.ole
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: e1d6be9687085361edd9141d8fb471e21b6f6376
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59038682"
---
# <a name="ole-db-provider-templates-reference"></a>Referencia de plantillas de proveedores OLE DB

Las clases e interfaces para las plantillas de proveedor OLE DB se pueden agrupar en las siguientes categorías. El material de referencia también incluye información sobre la [macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Las clases usan la convención de nomenclatura siguiente: una clase denominada con el patrón `IWidgetImpl` proporcionaría una implementación de la interfaz `IWidget`.

## <a name="session-classes"></a>Clases de la sesión

[IDBCreateSessionImpl](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Crea una nueva sesión desde el objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada. Interfaz obligatoria en los objetos de origen de datos.

[ISessionPropertiesImpl](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Propiedades de la sesión se implementa mediante una llamada a una función estática definida por la asignación de conjunto de propiedades. La asignación de conjunto de propiedades se debe especificar en la clase de sesión. Interfaz obligatoria en las sesiones.

## <a name="rowset-classes"></a>Clases de conjunto de filas

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Proporciona una implementación de conjunto de filas de OLE DB estándar sin necesidad de herencia múltiple de cuántas interfaces de implementación. El único método para el que debe proporcionar la implementación es `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en la `IRowsetImpl` clase. Identificador de fila es, lógicamente, una etiqueta única para una fila de resultados. `IRowsetImpl` crea un nuevo `CSimpleRow` para todas las filas solicitaron en `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB requiere que los proveedores implementar un `HACCESSOR`, que es una etiqueta a una matriz de `DBBINDING` estructuras. Proporciona `HACCESSOR`s que son direcciones de la `BindType` estructuras. Obligatorio en los conjuntos de filas y los comandos.

[IColumnsInfoImpl](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Delega en una función estática definidas por la asignación de columna del proveedor. Interfaz obligatoria en los conjuntos de filas y los comandos.

[IConvertTypeImpl](../../data/oledb/iconverttypeimpl-class.md)<br/>
Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas. Obligatorio en los comandos, los conjuntos de filas y conjuntos de filas de índice. Implementa el `IConvertType` interfaz delegando al objeto de conversión proporcionado por OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementa el `IDBSchemaRowset` interfaz y la función de creador de plantillas `CreateSchemaRowset`.

[IOpenRowsetImpl](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Se abre y devuelve un conjunto de filas que incluye todas las filas de una única tabla base o índice. Interfaz obligatoria para un objeto de sesión.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementa OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) interfaz, lo que permite la actualización de los valores de columnas en las filas existentes, eliminar filas y la inserción de nuevas filas.

[IRowsetCreatorImpl](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Esta clase hereda de [IObjectWithSite](/windows/desktop/api/ocidl/nn-ocidl-iobjectwithsite) e invalida [IObjectWithSite::SetSite](/windows/desktop/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` realiza las mismas funciones que `IObjectWithSite` , pero también permite que las propiedades de OLE DB `DBPROPCANSCROLLBACKWARDS` y `DBPROPCANFETCHBACKWARDS`.

[IRowsetIdentityImpl](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implementa el `IRowsetIdentity` interfaz, que le permite comparar si dos filas de datos son idénticas o no.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Proporciona una implementación de la `IRowset` interfaz, que es la interfaz base del conjunto de filas.

[IRowsetInfoImpl](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementa las propiedades del conjunto de filas mediante la propiedad conjunto de asignación definida en la clase de comando. Interfaz obligatoria en conjuntos de filas.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementa OLE DB [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) interfaz, que recupera filas arbitrarias de un conjunto de filas. Para admitir los marcadores de OLE DB en un conjunto de filas, hacer el conjunto de filas que herede de esta clase.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementa funciones para advertir a los agentes de escucha en el punto de conexión de difusión `IID_IRowsetNotify` de los cambios en el contenido del conjunto de filas. Los consumidores que controlan las notificaciones implementan [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) y regístrelo en ese punto de conexión.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementa OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) interfaz, que permite a los consumidores retrasar la transmisión de los cambios realizados con [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) al origen de datos y deshacer los cambios antes de la transmisión.

## <a name="command-classes"></a>Clases de comandos

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Proporciona una implementación de la interfaz `ICommand`. Esta interfaz no está visible, pero se controla mediante `ICommandTextImpl`. Una interfaz obligatoria en el objeto de comando.

[ICommandPropertiesImpl](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Esta implementación de la `ICommandProperties` interfaz proporciona una función estática definida por el `BEGIN_PROPSET_MAP` macro. Obligatorio en los comandos.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Establece, almacena y devuelve el texto del comando. Obligatorio en los comandos.

[IDBCreateCommandImpl](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Crea un nuevo comando desde el objeto de sesión y devuelve la interfaz solicitada en el comando recién creado. Interfaz opcional en los objetos de sesión.

Otras clases de comando son `IColumnsInfoImpl` y `IAccessorImpl`, que se describen en la sección de las clases de conjunto de filas anterior.

## <a name="data-source-classes"></a>Clases de origen de datos

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Crea y elimina la conexión con el consumidor. Interfaz obligatoria en los objetos de origen de datos y una interfaz opcional sobre los enumeradores.

[IDBPropertiesImpl](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` es una interfaz obligatoria para los objetos de origen de datos y una interfaz opcional para los enumeradores. Sin embargo, si expone un enumerador `IDBInitialize`, debe exponer `IDBProperties` (propiedades del origen de datos).

[IGetDataSourceImpl](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Obtiene un puntero de interfaz al objeto de origen de datos. Interfaz obligatoria en la sesión.

## <a name="other-classes"></a>Otras clases

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implementa las propiedades para una variedad de interfaces de la propiedad de OLE DB (por ejemplo, `IDBProperties`, `ISessionProperties`, y `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implementa OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) interfaz, agregar registros a y recuperar registros de un miembro de datos.

## <a name="see-also"></a>Vea también

[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[plantillas OLE DB](../../data/oledb/ole-db-templates.md)