---
title: Compatibilidad con bases de datos, Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: c13d56d2fee45e130aba81168188bec6d8828d51
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365881"
---
# <a name="database-support-mfc-application-wizard"></a>Compatibilidad con bases de datos, Asistente para aplicaciones MFC

Esta página proporciona opciones que le permiten especificar el nivel de compatibilidad de la base de datos (además de un origen de datos, si es necesario) para el proyecto.

- **Soporte de bases de datos**

   Establece el nivel de compatibilidad de la base de datos para el proyecto.

   |Opción|Descripción|
   |------------|-----------------|
   |**None**|No proporciona compatibilidad con bases de datos. Ésta es la opción predeterminada.|
   |**Sólo archivos de encabezado**|Proporciona el nivel básico de compatibilidad con la base de datos para la aplicación. Si selecciona Compatibilidad con ODBC en Tipo de **cliente**, el Asistente para aplicaciones MFC incluye en el proyecto el archivo de encabezado AFXDB. H. Agrega bibliotecas de vínculos, pero no crea ninguna clase específica de la base de datos. Puede crear conjuntos de registros más adelante y usarlos para examinar y actualizar registros. Si selecciona Compatibilidad con OLE DB en **Tipo de cliente**, se incluyen los siguientes archivos de encabezado: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Vista de base de datos sin soporte de archivos**|Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de compatibilidad con **arquitectura de documento/vista** seleccionada en la página [Tipo](../../mfc/reference/application-type-mfc-application-wizard.md) de aplicación.) Esta opción incluye compatibilidad con documentos, pero no compatibilidad con serialización. Si decide incluir una vista de base de datos, debe especificar el origen de los datos.|
   |**Vista de base de datos con soporte de archivos**|Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para aplicaciones con la opción de compatibilidad con **arquitectura de documento/vista** seleccionada en la página **Tipo** de aplicación.) Esta opción admite la serialización de documentos, que puede usar, por ejemplo, para actualizar un archivo de perfil de usuario. Las aplicaciones de base de datos suelen funcionar por registro en lugar de por archivo, por lo que no necesitan serialización. Sin embargo, puede tener un uso especial para la serialización. Si decide incluir una vista de base de datos, debe especificar el origen de los datos.|

   > [!NOTE]
   > En **Compatibilidad con**base de datos , si selecciona Vista de base de datos **sin compatibilidad con** archivos o Vista de base de datos con compatibilidad **con**archivos , la derivación de la clase de vista difiere, en función de la selección de tipo de **cliente,** como se indica a continuación:

  - Si selecciona **ODBC** en **Tipo de cliente**, la clase de vista de la aplicación deriva de [CRecordView](../../mfc/reference/crecordview-class.md). Esta clase está asociada a una clase derivada de [CRecordset,](../../mfc/reference/crecordset-class.md)que el Asistente para aplicaciones MFC también crea automáticamente. Esta opción proporciona una aplicación basada en formularios en la que se usa la vista de registros para ver y actualizar registros a través de su conjunto de registros.

  - Si selecciona **OLE DB** en Tipo de **cliente**, la clase de vista deriva de [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md)y está asociada a una clase derivada de [CTable](../../data/oledb/ctable-class.md) o [CCommand](../../data/oledb/ccommand-class.md).

- **Tipo de cliente**

   Indica si el proyecto utiliza clases OLE DB u ODBC.

   |Opción|Descripción|
   |------------|-----------------|
   |**OLE DB**|Cuando se selecciona esta opción, al hacer clic en el botón **Origen** de datos se invoca el asistente Propiedades de **vínculo** de datos para ayudarle a crear una conexión a un origen de datos OLE DB.|
   |**ODBC**|Cuando se selecciona esta opción, al hacer clic en el botón **Origen** de datos se invoca el asistente **Seleccionar origen** de datos para ayudarle a crear una conexión a un origen de datos ODBC.|

- **Fuente de datos**

   > [!NOTE]
   > El Asistente para consumidores OLE DB ATL y el Asistente para consumidores ODBC de MFC no están disponibles en Visual Studio 2019 y versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](../../data/oledb/creating-a-consumer-without-using-a-wizard.md).

   Haga clic en el botón **Origen** de datos para configurar un origen de datos mediante el controlador o proveedor y la base de datos especificados. Si seleccionó OLE DB en la opción Tipo de **cliente,** este botón muestra el cuadro de diálogo Propiedades de **vínculo** de datos. Si seleccionó ODBC en la opción Tipo de **cliente,** este botón proporciona el cuadro de diálogo Seleccionar origen de **datos.** Esta opción solo está disponible si elige incluir una vista de base de datos en la aplicación.

   |Opción|Descripción|
   |------------|-----------------|
   |**Propiedades de vínculo** de datos (OLE DB)|Establece el origen de datos especificado mediante el proveedor OLE DB especificado. Debe especificar el proveedor OLE DB, la ubicación de los datos, el origen de datos, el identificador de inicio de sesión y (opcionalmente) una contraseña. Para obtener más información sobre este cuadro de diálogo, vea **Origen de datos** en el Asistente para [consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Seleccionar origen de datos** (ODBC)|Establece el origen de datos especificado mediante el controlador ODBC especificado. Debe seleccionar un nombre de origen de datos para elegir una tabla para el origen de datos. El asistente enlaza todas las columnas de la `CRecordset`tabla a las variables miembro de una clase derivada. Para obtener más información sobre este cuadro de diálogo, vea **Origen de datos** en el Asistente para [consumidores ODBC](../../mfc/reference/mfc-odbc-consumer-wizard.md)de MFC .|

- **Generar clase de base de datos con atributos**

   Disponible solo para cliente OLE DB. Especifica si las clases de base de datos en los atributos de uso del proyecto generado.

- **Enlazar todas las columnas**

   Disponible solo para el cliente ODBC. Especifica si todas las columnas de la tabla seleccionada están enlazadas. Si selecciona este cuadro, todas las columnas están enlazadas; si no selecciona este cuadro, no se enlaza ninguna columna y debe enlazarlas manualmente en la clase de conjunto de registros.

- **Tipo**

   Disponible solo para el cliente ODBC. Especifica si el conjunto de registros es un conjunto de registros dinámicos o una instantánea, como se describe en la tabla siguiente.

   |Opción|Descripción|
   |------------|-----------------|
   |**Conjunto de registros dinámicos**|Especifica que el conjunto de registros es un conjunto de registros dinámicos. Un conjunto de registros dinámicos es el resultado de una consulta que proporciona una vista indizada en los datos de la base de datos consultada. Un conjunto de registros dinámicos almacena en caché solo un índice integral de los datos originales y, por lo tanto, ofrece una ganancia de rendimiento sobre una instantánea. El índice apunta directamente a cada registro encontrado como resultado de una consulta e indica si se quita un registro. También tiene acceso a información actualizada en los registros consultados.|
   |**Instantánea**|Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá ningún cambio en los registros originales.|

## <a name="see-also"></a>Consulte también

[Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)
