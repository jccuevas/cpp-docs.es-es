---
title: Compatibilidad con bases de datos, Asistente para aplicaciones MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.database
helpviewer_keywords:
- MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
ms.openlocfilehash: a1e0519e1351a48bbd969168d62f163c9dde7e7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57259963"
---
# <a name="database-support-mfc-application-wizard"></a>Compatibilidad con bases de datos, Asistente para aplicaciones MFC

Esta página proporciona opciones que le permiten especificar el nivel de base de datos admite (además de un origen de datos, si es necesario) para el proyecto.

- **Compatibilidad con la base de datos**

   Establece el nivel de compatibilidad de base de datos para el proyecto.

   |Opción|Descripción|
   |------------|-----------------|
   |**Ninguno**|No proporciona ninguna compatibilidad de base de datos. Ésta es la opción predeterminada.|
   |**Archivos de encabezado**|Proporciona el nivel básico de compatibilidad de base de datos para la aplicación. Si selecciona compatibilidad con ODBC en **tipo cliente**, MFC Application Wizard se incluye en el proyecto el archivo de encabezado AFXDB. H. Agrega las bibliotecas de vínculos, pero no crea todas las clases de base de datos específica. Puede crear conjuntos de registros más adelante y usarlos para examinar y actualizar registros. Si selecciona compatibilidad con OLE DB en **tipo cliente**, se incluyen los archivos de encabezado siguientes: ATLBASE. H AFXOLEDB. H ATLPLUS. H|
   |**Vista de base de datos sin compatibilidad con archivos**|Incluye archivos de encabezado de la base de datos, las bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para las aplicaciones con el **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página.) Esta opción incluye compatibilidad con documentos pero no con la serialización. Si decide incluir una vista de base de datos, debe especificar el origen de datos.|
   |**Vista de base de datos con compatibilidad con archivos**|Incluye archivos de encabezado de la base de datos, las bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible solo para las aplicaciones con el **compatibilidad con la arquitectura documento/vista** opción seleccionada en el **tipo de aplicación** página.) Esta opción admite la serialización de documentos, que puede usar, por ejemplo, para actualizar un archivo de perfil de usuario. Las aplicaciones de base de datos se suelen aplicar a una base por registro en lugar de en un archivo por lo que no necesitan la serialización. Sin embargo, puede tener un uso especial para la serialización. Si decide incluir una vista de base de datos, debe especificar el origen de datos.|

   > [!NOTE]
   > En **base de datos admite**, si selecciona alguna **vista sin compatibilidad con archivos de base de datos** o **vista con compatibilidad con archivos de base de datos**, difiere de la derivación de clase de vista, función en su **tipo cliente** selección, como se indica a continuación:

   - Si selecciona **ODBC** en **tipo cliente**, a continuación, se deriva de la clase de vista de la aplicación [CRecordView](../../mfc/reference/crecordview-class.md). Esta clase está asociada con un [CRecordset](../../mfc/reference/crecordset-class.md)-clase derivada, que también se crea el Asistente para aplicaciones MFC para usted. Esta opción proporciona una aplicación basada en formularios en el que se usa la vista de registros para ver y actualizar registros a través de su conjunto de registros.

   - Si selecciona **OLE DB** en **tipo de cliente**, a continuación, se deriva de la clase de vista [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), y se asocia un [CTable](../../data/oledb/ctable-class.md) o [CCommand](../../data/oledb/ccommand-class.md)-clase derivada.

- **Tipo de cliente**

   Indica si el proyecto usa las clases de OLE DB u ODBC.

   |Opción|Descripción|
   |------------|-----------------|
   |**OLE DB**|Cuando se selecciona esta opción, haga clic en el **origen de datos** botón invoca el **propiedades de vínculo de datos** asistente que le ayudarán a crear una conexión a un origen de datos OLE DB.|
   |**ODBC**|Cuando se selecciona esta opción, haga clic en el **origen de datos** botón invoca el **Seleccionar origen de datos** asistente que le ayudarán a crear una conexión a un origen de datos ODBC.|

- **Origen de datos**

   Haga clic en el **origen de datos** botón para configurar un origen de datos mediante el controlador especificado o el proveedor y la base de datos. Si seleccionó OLE DB en el **tipo cliente** muestra este botón de opción, el **propiedades de vínculo de datos** cuadro de diálogo. Si seleccionó ODBC en el **tipo cliente** opción que proporciona este botón el **Seleccionar origen de datos** cuadro de diálogo. Esta opción está disponible solo si elige incluir una vista de base de datos en la aplicación.

   |Opción|Descripción|
   |------------|-----------------|
   |**Propiedades de vínculo de datos** (OLE DB)|Establece el origen de datos especificado mediante el proveedor OLE DB especificado. Debe especificar el proveedor OLE DB, la ubicación de los datos, el origen de datos, Id. de inicio de sesión y (opcionalmente) una contraseña. Para obtener más información sobre este cuadro de diálogo, vea **origen de datos** en [el Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|
   |**Seleccionar origen de datos** (ODBC)|Establece el origen de datos especificado mediante el controlador ODBC especificado. Debe seleccionar un nombre de origen de datos para elegir una tabla del origen de datos. El Asistente enlaza a todas las columnas de la tabla a las variables de miembro de un `CRecordset`-clase derivada. Para obtener más información sobre este cuadro de diálogo, vea **origen de datos** en [Asistente para consumidores ODBC de MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|

   > [!NOTE]
   > En versiones anteriores, MAYÚS y haciendo clic en el **origen de datos** botón abre un cuadro de diálogo Abrir archivo para que pueda seleccionar un archivo de Data Link (.udl). Ya no se admite esta funcionalidad.

- **Generar clase con atributos de la base de datos**

   Está disponible para el cliente solo de OLE DB. Especifica si las clases de base de datos en el proyecto generado utilizan atributos.

- **Enlazar todas las columnas**

   Está disponible para el cliente solo de ODBC. Especifica si todas las columnas de la tabla seleccionada están enlazadas. Si activa esta casilla, se enlazan todas las columnas; Si no selecciona esta casilla, no hay columnas se enlazan y debe enlazar manualmente en la clase de conjunto de registros.

- **Type**

   Está disponible para el cliente solo de ODBC. Especifica si el conjunto de registros es de tipo dinámico o una instantánea, tal como se describe en la tabla siguiente.

   |Opción|Descripción|
   |------------|-----------------|
   |**Conjunto de registros dinámicos**|Especifica que el conjunto de registros es de tipo dinámico. Tipo dinámico es el resultado de una consulta que proporciona una vista indizada en datos la base de consultada. Un conjunto de registros dinámicos almacena en caché sólo un índice entero para los datos originales y, por tanto, ofrece un rendimiento descanse una instantánea. El índice apunta directamente a cada registro encontrados como resultado de una consulta y se indica si se quita un registro. También tendrá acceso a la información actualizada en los registros consultados.|
   |**Instantánea**|Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá los cambios realizados en los registros originales.|

## <a name="see-also"></a>Vea también

[Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)
