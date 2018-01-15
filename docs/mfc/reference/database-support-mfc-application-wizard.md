---
title: Base de datos, Asistente para aplicaciones MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.appwiz.mfc.exe.database
dev_langs: C++
helpviewer_keywords: MFC Application Wizard, database support
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7b7c9aaa6389f5e86a51348a8b5423260c4c76e3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="database-support-mfc-application-wizard"></a>Compatibilidad con bases de datos, Asistente para aplicaciones MFC
Esta página proporciona opciones que le permiten especificar el nivel de base de datos admite (más de un origen de datos, si es necesario) para el proyecto.  
  
 **Compatibilidad de base de datos**  
 Establece el nivel de compatibilidad de base de datos para el proyecto.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Ninguno**|No proporciona ninguna compatibilidad de base de datos. Ésta es la opción predeterminada.|  
|**Sólo los archivos de encabezado**|Proporciona el nivel básico de compatibilidad de base de datos para la aplicación. Si selecciona compatibilidad con ODBC en **tipo cliente**, el Asistente para aplicaciones MFC incluye en el proyecto, el archivo de encabezado AFXDB. H. Agrega bibliotecas de vínculos, pero no crea las clases específicas de la base de datos. También puede crear conjuntos de registros más tarde y usarlos para examinar y actualizar registros. Si selecciona la compatibilidad con OLE DB en **tipo cliente**, se incluyen los siguientes archivos de encabezado: ATLBASE. H AFXOLEDB. H ATLPLUS. H|  
|**Vista de base de datos sin compatibilidad con archivos**|Incluye archivos de encabezado de la base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible únicamente para las aplicaciones con la **compatibilidad con la arquitectura documento/vista** opción seleccionada en el [tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md) página.) Esta opción incluye compatibilidad con documentos pero no hay compatibilidad con la serialización. Si elige incluir una vista de base de datos, debe especificar el origen de los datos.|  
|**Vista de base de datos con compatibilidad con archivos**|Incluye archivos de encabezado de la base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. (Disponible únicamente para las aplicaciones con la **compatibilidad con la arquitectura documento/vista** opción seleccionada en el **tipo de aplicación** página.) Esta opción admite la serialización de documentos, que puede usar, por ejemplo, para actualizar un archivo de perfil de usuario. Las aplicaciones de base de datos suelen funcionan en una base por registro en lugar de en un archivo por base de modo que no necesitan la serialización. Sin embargo, puede tener un uso especial para la serialización. Si elige incluir una vista de base de datos, debe especificar el origen de los datos.|  
  
> [!NOTE]
>  En **base de datos admite**, si selecciona una de ellas **vista sin compatibilidad con archivos de base de datos** o **vista con compatibilidad con archivos de base de datos**, difiere de la derivación de la clase de vista, función en su **tipo cliente** selección, como se indica a continuación:  
  
-   Si selecciona **ODBC** en **tipo cliente**, a continuación, clase de vista de la aplicación se deriva de [CRecordView](../../mfc/reference/crecordview-class.md). Esta clase está asociada con un [CRecordset](../../mfc/reference/crecordset-class.md)-clase derivada, que el Asistente para aplicaciones MFC también se crea automáticamente. Esta opción proporciona una aplicación basada en formularios en el que se usa la vista de registros para ver y actualizar registros a través de su conjunto de registros.  
  
-   Si selecciona **OLE DB** en **tipo cliente**, a continuación, la clase de vista se deriva de [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md), y que está asociado un [CTable](../../data/oledb/ctable-class.md) o [CCommand](../../data/oledb/ccommand-class.md)-clase derivada.  
  
 **Tipo de cliente**  
 Indica si el proyecto utiliza clases OLE DB u ODBC.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**OLE DB**|Cuando se selecciona esta opción, haga clic en el **origen de datos** botón, se invoca el **propiedades de vínculo de datos** Asistente para ayudarle a crear una conexión a un origen de datos OLE DB.|  
|**ODBC**|Cuando se selecciona esta opción, haga clic en el **origen de datos** botón, se invoca el **Seleccionar origen de datos** Asistente para ayudarle a crear una conexión a un origen de datos ODBC.|  
  
 **Origen de datos**  
 Haga clic en el **origen de datos** botón para configurar un origen de datos mediante el controlador especificado o el proveedor y la base de datos. Si seleccionó OLE DB en el **tipo cliente** muestra de este botón de opción, el **propiedades de vínculo de datos** cuadro de diálogo. Si seleccionó ODBC en el **tipo cliente** opción, este botón proporciona el **Seleccionar origen de datos** cuadro de diálogo. Esta opción está disponible sólo si elige incluir una vista de base de datos en la aplicación.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Propiedades de vínculo de datos** (OLE DB)|Establece el origen de datos especificado mediante el proveedor OLE DB especificado. Debe especificar el proveedor OLE DB, la ubicación de los datos, el origen de datos, Id. de inicio de sesión y (opcionalmente) una contraseña. Para obtener detalles sobre este cuadro de diálogo, vea **origen de datos** en [el Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
|**Seleccionar origen de datos** (ODBC)|Establece el origen de datos especificado mediante el controlador ODBC especificado. Debe seleccionar un nombre de origen de datos para elegir una tabla del origen de datos. El Asistente enlazará todas las columnas de la tabla a las variables de miembro de un `CRecordset`-clase derivada. Para obtener detalles sobre este cuadro de diálogo, vea **origen de datos** en [Asistente para consumidores ODBC de MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
> [!NOTE]
>  En versiones anteriores, MAYÚS y haciendo clic en el **origen de datos** botón abre un cuadro de diálogo Abrir archivo para que pueda seleccionar un archivo de Data Link (.udl). Ya no se admite esta funcionalidad.  
  
 **Generar clase de base de datos con atributos**  
 Está disponible para el cliente solo de OLE DB. Especifica si las clases de base de datos en el proyecto generado utilizan atributos.  
  
 **Enlazar todas las columnas**  
 Está disponible para el cliente solo de ODBC. Especifica si se enlazan todas las columnas de la tabla seleccionada. Si activa esta casilla, se enlazan todas las columnas; Si no activa esta casilla, se enlaza ninguna columna y deberá enlazarlas manualmente en la clase de conjunto de registros.  
  
 **Type**  
 Está disponible para el cliente solo de ODBC. Especifica si el conjunto de registros es un conjunto de registros dinámicos o una instantánea, tal como se describe en la tabla siguiente.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Conjunto de registros dinámicos**|Especifica que el conjunto de registros es un conjunto de registros dinámicos. Un conjunto de registros dinámicos es el resultado de una consulta que proporciona una vista indizada en datos la base de consultada. Un conjunto de registros dinámicos se almacena en memoria caché solo un índice entero a los datos originales y, por tanto, ofrece un rendimiento obtener a través de una instantánea. El índice apunta directamente a cada registro encontrados como resultado de una consulta y se indica si se elimina un registro. También tienen acceso a la información actualizada en los registros consultados.|  
|Instantánea|Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un punto en el tiempo. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá los cambios realizados en los registros originales.|  
  
## <a name="see-also"></a>Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)
