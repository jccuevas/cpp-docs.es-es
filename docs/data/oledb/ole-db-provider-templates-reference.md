---
title: Referencia de plantillas de proveedores OLE DB
ms.date: 11/04/2016
helpviewer_keywords:
- OLE DB provider templates
ms.assetid: 518358f0-bab1-4de9-bce9-4062cc87c11f
ms.openlocfilehash: f0200f0cff5292a75ec853496a644c148c8356a3
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545796"
---
# <a name="ole-db-provider-templates-reference"></a>Referencia de plantillas de proveedores OLE DB

Las clases e interfaces para las plantillas de proveedor de OLE DB se pueden agrupar en las categorías siguientes. El material de referencia también incluye información sobre las [macros para las plantillas de proveedor de OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md).

Las clases usan la Convención de nomenclatura siguiente: una clase denominada con el patrón `IWidgetImpl` proporcionaría una implementación de la interfaz `IWidget`.

## <a name="session-classes"></a>Clases de sesión

[Idbcreatesessionimpl (](../../data/oledb/idbcreatesessionimpl-class.md)<br/>
Crea una nueva sesión a partir del objeto de origen de datos y devuelve la interfaz solicitada en la sesión recién creada. Interfaz obligatoria en los objetos de origen de datos.

[Isessionpropertiesimpl (](../../data/oledb/isessionpropertiesimpl-class.md)<br/>
Implementa las propiedades de la sesión mediante una llamada a una función estática definida por la asignación del conjunto de propiedades. La asignación del conjunto de propiedades debe especificarse en la clase de sesión. Interfaz obligatoria en las sesiones.

## <a name="rowset-classes"></a>Clases de conjunto de filas

[CRowsetImpl](../../data/oledb/crowsetimpl-class.md)

Proporciona una implementación de conjunto de filas de OLE DB estándar sin requerir la herencia múltiple de muchas interfaces de implementación. El único método para el que se debe proporcionar la implementación es `Execute`.

[CSimpleRow](../../data/oledb/csimplerow-class.md)<br/>
Proporciona una implementación predeterminada para el identificador de fila, que se utiliza en la clase `IRowsetImpl`. Un identificador de fila es lógicamente una etiqueta única para una fila de resultados. `IRowsetImpl` crea un `CSimpleRow` nuevo para cada fila solicitada en `IRowsetImpl::GetNextRows`.

[IAccessorImpl](../../data/oledb/iaccessorimpl-class.md)<br/>
OLE DB requiere que los proveedores implementen una `HACCESSOR`, que es una etiqueta para una matriz de estructuras `DBBINDING`. Proporciona `HACCESSOR`s que son direcciones de las estructuras de `BindType`. Obligatorio en conjuntos de filas y comandos.

[Icolumnsinfoimpl (](../../data/oledb/icolumnsinfoimpl-class.md)<br/>
Delega en una función estática definida por el mapa de columnas del proveedor. Interfaz obligatoria en conjuntos de filas y comandos.

[Iconverttypeimpl (](../../data/oledb/iconverttypeimpl-class.md)<br/>
Proporciona información sobre la disponibilidad de las conversiones de tipos en un comando o en un conjunto de filas. Obligatorio en los comandos, conjuntos de filas y conjuntos de filas de índice. Implementa la interfaz de `IConvertType` delegando en el objeto de conversión proporcionado por OLE DB.

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md)<br/>
Implementa la interfaz de `IDBSchemaRowset` y la función hace plantilla Creator `CreateSchemaRowset`.

[Iopenrowsetimpl (](../../data/oledb/iopenrowsetimpl-class.md)<br/>
Abre y devuelve un conjunto de filas que incluye todas las filas de una sola tabla base o índice. Interfaz obligatoria para un objeto de sesión.

[IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md)<br/>
Implementa la interfaz OLE DB [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) , que permite actualizar los valores de las columnas de las filas existentes, eliminar filas e insertar nuevas filas.

[Irowsetcreatorimpl (](../../data/oledb/irowsetcreatorimpl-class.md)<br/>
Esta clase hereda de [IObjectWithSite](/windows/win32/api/ocidl/nn-ocidl-iobjectwithsite) e invalida [IObjectWithSite:: SetSite](/windows/win32/api/ocidl/nf-ocidl-iobjectwithsite-setsite). `IRowsetCreatorImpl` realiza las mismas funciones que `IObjectWithSite` pero también habilita las propiedades OLE DB `DBPROPCANSCROLLBACKWARDS` y `DBPROPCANFETCHBACKWARDS`.

[Irowsetidentityimpl (](../../data/oledb/irowsetidentityimpl-class.md)<br/>
Implementa la interfaz de `IRowsetIdentity`, que permite comparar si dos filas de datos son idénticas o no.

[IRowsetImpl](../../data/oledb/irowsetimpl-class.md)<br/>
Proporciona una implementación de la interfaz de `IRowset`, que es la interfaz de conjunto de filas base.

[Irowsetinfoimpl (](../../data/oledb/irowsetinfoimpl-class.md)<br/>
Implementa las propiedades del conjunto de filas mediante el mapa de conjuntos de propiedades definido en la clase de comando. Interfaz obligatoria en conjuntos de filas.

[IRowsetLocateImpl](../../data/oledb/irowsetlocateimpl-class.md)<br/>
Implementa el OLE DB interfaz [IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85)) , que captura filas arbitrarias de un conjunto de filas. Para admitir OLE DB marcadores en un conjunto de filas, haga que el conjunto de filas herede de esta clase.

[IRowsetNotifyCP](../../data/oledb/irowsetnotifycp-class.md)<br/>
Implementa funciones de difusión para informar a los agentes de escucha en el punto de conexión `IID_IRowsetNotify` de los cambios en el contenido del conjunto de filas. Los consumidores que controlan las notificaciones implementan [IRowsetNotify](/previous-versions/windows/desktop/ms712959(v=vs.85)) y lo registran en ese punto de conexión.

[IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md)<br/>
Implementa la interfaz OLE DB [IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85)) , que permite a los consumidores retrasar la transmisión de los cambios realizados con [IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85)) al origen de datos y deshacer los cambios antes de la transmisión.

## <a name="command-classes"></a>Clases de comandos

[ICommandImpl](../../data/oledb/icommandimpl-class.md)<br/>
Proporciona una implementación de la interfaz `ICommand`. Esta interfaz no es visible, pero la controla `ICommandTextImpl`. Interfaz obligatoria en el objeto de comando.

[Icommandpropertiesimpl (](../../data/oledb/icommandpropertiesimpl-class.md)<br/>
Esta implementación de la interfaz `ICommandProperties` se proporciona mediante una función estática definida por la macro `BEGIN_PROPSET_MAP`. Obligatorio en los comandos.

[ICommandTextImpl](../../data/oledb/icommandtextimpl-class.md)<br/>
Establece, almacena y devuelve el texto del comando. Obligatorio en los comandos.

[Idbcreatecommandimpl (](../../data/oledb/idbcreatecommandimpl-class.md)<br/>
Crea un nuevo comando a partir del objeto de sesión y devuelve la interfaz solicitada en el comando recién creado. Interfaz opcional en objetos de sesión.

Otras clases de comandos son `IColumnsInfoImpl` y `IAccessorImpl`, descritas en la sección de clases de conjunto de filas anterior.

## <a name="data-source-classes"></a>Clases de origen de datos

[IDBInitializeImpl](../../data/oledb/idbinitializeimpl-class.md)<br/>
Crea y elimina la conexión con el consumidor. Interfaz obligatoria en los objetos de origen de datos y la interfaz opcional en los enumeradores.

[Idbpropertiesimpl (](../../data/oledb/idbpropertiesimpl-class.md)<br/>
`IDBProperties` es una interfaz obligatoria para los objetos de origen de datos y una interfaz opcional para los enumeradores. Sin embargo, si un enumerador expone `IDBInitialize`, debe exponer `IDBProperties` (propiedades en el origen de datos).

[Igetdatasourceimpl (](../../data/oledb/igetdatasourceimpl-class.md)<br/>
Obtiene un puntero de interfaz al objeto de origen de datos. Interfaz obligatoria en la sesión.

## <a name="other-classes"></a>Otras clases

[CUtlProps](../../data/oledb/cutlprops-class.md)<br/>
Implementa propiedades para una variedad de interfaces de propiedad OLE DB (por ejemplo, `IDBProperties`, `ISessionProperties`y `IRowsetInfo`).

[IErrorRecordsImpl](../../data/oledb/ierrorrecordsimpl-class.md)

Implementa la interfaz OLE DB [IErrorRecords](/previous-versions/windows/desktop/ms718112(v=vs.85)) , agregando registros y recuperando registros de un miembro de datos.

## <a name="see-also"></a>Consulte también

[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[Plantillas OLE DB](../../data/oledb/ole-db-templates.md)