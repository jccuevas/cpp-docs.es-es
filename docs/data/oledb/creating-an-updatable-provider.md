---
title: Crear un proveedor actualizable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, updatable
- notifications, support in providers
- OLE DB providers, creating
ms.assetid: bdfd5c9f-1c6f-4098-822c-dd650e70ab82
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e9ee36d2300ed1e86c1f867012ed54c85692f5bd
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340643"
---
# <a name="creating-an-updatable-provider"></a>Crear un proveedor actualizable

Visual C++ admite proveedores actualizables o que se puede actualizar (escribir en) el almacén de datos. En este tema se describe cómo crear proveedores actualizables mediante plantillas OLE DB.  
  
 En este tema se da por supuesto que empieza con un proveedor viable. Hay dos pasos para crear un proveedor actualizable. Primero debe decidir cómo el proveedor realizará cambios en el almacén de datos; en concreto, si los cambios deben realizarse inmediatamente o aplaza hasta que se emite un comando de actualización. La sección "[convertir proveedores actualizables](#vchowmakingprovidersupdatable)" se describen los cambios y configuración que necesita hacer en el código del proveedor.  
  
 A continuación, debe asegurarse de que su proveedor contiene toda la funcionalidad para admitir cualquier cosa que el consumidor puede solicitar del mismo. Si el consumidor desea actualizar el almacén de datos, el proveedor debe contener código que conserva los datos en el almacén de datos. Por ejemplo, podría usar la biblioteca de tiempo de ejecución de C o MFC para realizar esas operaciones en el origen de datos. La sección "[escribir en el origen de datos](#vchowwritingtothedatasource)" se describe cómo escribir en el origen de datos, tratar los valores NULL y el valor predeterminado y establecer marcadores de columna.  
  
> [!NOTE]
>  UpdatePV es un ejemplo de un proveedor actualizable. UpdatePV es el mismo como MyProv pero compatibilidad con la actualización.  
  
##  <a name="vchowmakingprovidersupdatable"></a> Hacer que los proveedores actualizables  

 La clave para crear un proveedor actualizable es comprender las operaciones que desea que el proveedor para realizar en el almacén de datos y cómo desea que el proveedor para llevar a cabo esas operaciones. En concreto, el problema principal es que si están las actualizaciones del almacén de datos que deben realizarse inmediatamente o se aplaza (por lotes) hasta que se emite un comando de actualización.  
  
 Primero debe decidir si va a heredar `IRowsetChangeImpl` o `IRowsetUpdateImpl` en la clase de conjunto de filas. Dependiendo de cuál de estos elija implementar, afectará la funcionalidad de los tres métodos: `SetData`, `InsertRows`, y `DeleteRows`.  
  
- Si se hereda de [IRowsetChangeImpl](../../data/oledb/irowsetchangeimpl-class.md), llamar a estos tres métodos inmediatamente los cambios del almacén de datos.  
  
- Si se hereda de [IRowsetUpdateImpl](../../data/oledb/irowsetupdateimpl-class.md), los métodos aplazan los cambios realizados en el almacén de datos hasta que llame a `Update`, `GetOriginalData`, o `Undo`. Si la actualización implica varios cambios, que se realizan en modo por lotes (tenga en cuenta que el procesamiento por lotes de cambios puede agregar una sobrecarga de memoria considerable).  
  
 Tenga en cuenta que `IRowsetUpdateImpl` deriva `IRowsetChangeImpl`. Por lo tanto, `IRowsetUpdateImpl` ofrece hacer cambios funcionalidad y capacidad de proceso por lotes.  
  
#### <a name="to-support-updatability-in-your-provider"></a>Para admitir la posibilidad de actualización en un proveedor  
  
1. En la clase de conjunto de filas, se heredan de `IRowsetChangeImpl` o `IRowsetUpdateImpl`. Estas clases proporcionan interfaces adecuadas para cambiar el almacén de datos:  
  
     **Agregar IRowsetChange**  
  
     Agregar `IRowsetChangeImpl` a la cadena de herencia de esta forma:  
  
    ```cpp  
    IRowsetChangeImpl< rowset-name, storage-name >  
    ```  
  
     También agregar `COM_INTERFACE_ENTRY(IRowsetChange)` a la `BEGIN_COM_MAP` sección en la clase de conjunto de filas.  
  
     **Agregar IRowsetUpdate**  
  
     Agregar `IRowsetUpdate` a la cadena de herencia de esta forma:  
  
    ```cpp  
    IRowsetUpdateImpl< rowset-name, storage>  
    ```  
  
    > [!NOTE]
    >  Debe quitar la `IRowsetChangeImpl` línea desde la cadena de herencia. Esta excepción a la Directiva mencionada anteriormente debe incluir el código para `IRowsetChangeImpl`.  
  
2.  Agregue lo siguiente al mapa COM (`BEGIN_COM_MAP ... END_COM_MAP`):  
  
    |Si implementa|Agregar al mapa COM|  
    |----------------------|--------------------|  
    |`IRowsetChangeImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)`|  
    |`IRowsetUpdateImpl`|`COM_INTERFACE_ENTRY(IRowsetChange)COM_INTERFACE_ENTRY(IRowsetUpdate)`|  
  
3.  En el comando, agregue lo siguiente a la asignación de conjunto de propiedades (`BEGIN_PROPSET_MAP ... END_PROPSET_MAP`):  
  
    |Si implementa|Agregar al mapa del conjunto de propiedades|  
    |----------------------|-----------------------------|  
    |`IRowsetChangeImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)`|  
    |`IRowsetUpdateImpl`|`PROPERTY_INFO_ENTRY_VALUE(IRowsetChange, VARIANT_FALSE)PROPERTY_INFO_ENTRY_VALUE(IRowsetUpdate, VARIANT_FALSE)`|  
  
4.  En la asignación de conjunto de propiedades, también debe incluir todos los valores siguientes que aparecen a continuación:  
  
    ```cpp  
    PROPERTY_INFO_ENTRY_VALUE(UPDATABILITY, DBPROPVAL_UP_CHANGE |   
      DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE)  
    PROPERTY_INFO_ENTRY_VALUE(CHANGEINSERTEDROWS, VARIANT_TRUE)  
    PROPERTY_INFO_ENTRY_VALUE(IMMOBILEROWS, VARIANT_TRUE)  
  
    PROPERTY_INFO_ENTRY_EX(OWNINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OWNUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERINSERT, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(OTHERUPDATEDELETE, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_TRUE, 0)  
    PROPERTY_INFO_ENTRY_EX(REMOVEDELETED, VT_BOOL, DBPROPFLAGS_ROWSET |   
      DBPROPFLAGS_READ, VARIANT_FALSE, 0)  
    ```  
  
     Puede encontrar los valores utilizados en estas llamadas a macros mediante una búsqueda en Atldb.h para los identificadores de propiedad y valores (si Atldb.h difiere de la documentación en línea, Atldb.h tiene prioridad sobre la documentación).  
  
    > [!NOTE]
    >  Muchos de los `VARIANT_FALSE` y `VARIANT_TRUE` ; indica que la especificación OLE DB pueden ser lectura/escritura, pero las plantillas OLE DB pueden admitir solo un valor de configuración es necesarios para las plantillas OLE DB.  
  
     **Si implementa IRowsetChangeImpl**  
  
     Si implementa `IRowsetChangeImpl`, debe establecer las siguientes propiedades en el proveedor. Estas propiedades se utilizan principalmente para solicitar interfaces a través de `ICommandProperties::SetProperties`.  
  
    - `DBPROP_IRowsetChange`: Esta acción automáticamente establecer establece `DBPROP_IRowsetChange`.  
  
    - `DBPROP_UPDATABILITY`: Una máscara de bits que especifica los métodos admitidos en `IRowsetChange`: `SetData`, `DeleteRows`, o `InsertRow`.  
  
    - `DBPROP_CHANGEINSERTEDROWS`: El consumidor puede llamar a `IRowsetChange::DeleteRows` o `SetData` para las filas recién insertadas.  
  
    - `DBPROP_IMMOBILEROWS`: El conjunto de filas no reordenará las filas insertadas o actualizadas.  
  
     **Si implementa IRowsetUpdateImpl**  
  
     Si implementa `IRowsetUpdateImpl`, debe establecer las siguientes propiedades en el proveedor, además a establecer todas las propiedades de `IRowsetChangeImpl` enumeradas anteriormente:  
  
    - `DBPROP_IRowsetUpdate`.  
  
    - `DBPROP_OWNINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    - `DBPROP_OWNUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    - `DBPROP_OTHERINSERT`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    - `DBPROP_OTHERUPDATEDELETE`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    - `DBPROP_REMOVEDELETED`: Debe ser READ_ONLY y VARIANT_TRUE.  
  
    - `DBPROP_MAXPENDINGROWS`.  
  
        > [!NOTE]
        >  Si se admiten las notificaciones, es posible que también tiene algunas otras propiedades; Consulte la sección sobre `IRowsetNotifyCP` para esta lista.  
  
##  <a name="vchowwritingtothedatasource"></a> Escribir en el origen de datos  
 Para leer desde el origen de datos, llame a la `Execute` función. Para escribir en el origen de datos, llame a la `FlushData` función. (En sentido general, vaciar significa guardar las modificaciones que realice en una tabla o índice en el disco).  

