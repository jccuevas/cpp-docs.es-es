---
title: "Compatibilidad con bases de datos, Asistente para aplicaciones MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.appwiz.mfc.exe.database"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para aplicaciones MFC, compatibilidad con bases de datos"
ms.assetid: 9ddf4558-fd41-4ac7-8d9b-c93d9c68ab59
caps.latest.revision: 9
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Compatibilidad con bases de datos, Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Esta página proporciona opciones que permiten especificar el nivel de compatibilidad con bases de datos \(y un origen de datos, si es necesario\) para el proyecto.  
  
 **Compatibilidad con bases de datos**  
 Establece el nivel de compatibilidad con bases de datos para el proyecto.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**None**|No proporciona compatibilidad con bases de datos.  Ésta es la opción predeterminada.|  
|**Sólo archivos de encabezado**|Proporciona el nivel básico de compatibilidad con bases de datos para la aplicación.<br /><br /> <ul><li>Si selecciona compatibilidad con ODBC en **Tipo de cliente**, el Asistente para aplicaciones MFC incluye en el proyecto el archivo de encabezado AFXDB.H.  Agrega bibliotecas de vínculos, pero no crea clases específicas de bases de datos.  Puede crear conjuntos de registros posteriormente y utilizarlos para examinar y actualizar registros.</li><li>Si selecciona compatibilidad con OLE DB en **Tipo de cliente**, se incluirán los siguientes archivos de encabezado:<br /><br /> <ul><li>ATLBASE.H</li><li>AFXOLEDB.H</li><li>ATLPLUS.H</li></ul></li></ul>|  
|**Vista de base de datos sin compatibilidad con archivos**|Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. Sólo está disponible para aplicaciones que tengan activada la opción **Compatibilidad con la arquitectura documento\/vista** en la página [Tipo de aplicación](../../mfc/reference/application-type-mfc-application-wizard.md). Esta opción incluye compatibilidad con documentos, pero no con la serialización.  Si elige incluir una vista de base de datos, debe especificar el origen de los datos.|  
|**Vista de base de datos con compatibilidad con archivos**|Incluye archivos de encabezado de base de datos, bibliotecas de vínculos, una vista de registros y un conjunto de registros. Sólo está disponible para aplicaciones que tengan activada la opción **Compatibilidad con la arquitectura documento\/vista** en la página **Tipo de aplicación**. Esta opción admite la serialización de documentos, que puede utilizar para actualizar un archivo de perfil de usuario, por ejemplo.  Las aplicaciones de base de datos suelen funcionar registro a registro, en lugar de archivo a archivo, por lo que no necesitan la serialización.  Sin embargo, es posible que tenga una necesidad especial de la serialización.  Si elige incluir una vista de base de datos, debe especificar el origen de los datos.|  
  
> [!NOTE]
>  En **Compatibilidad con bases de datos**, si selecciona **Vista de base de datos sin compatibilidad con archivos** o **Vista de base de datos con compatibilidad con archivos**, la derivación de la clase de vista varía en función de la selección de **Tipo de cliente**, como se indica a continuación:  
  
-   Si selecciona **ODBC** en **Tipo de cliente**, la clase de vista de la aplicación se deriva de [CRecordView](../../mfc/reference/crecordview-class.md).  Esta clase se asocia a una clase derivada de [CRecordset](../../mfc/reference/crecordset-class.md), que también crea automáticamente el Asistente para aplicaciones MFC.  Esta opción proporciona una aplicación basada en formularios en la que la vista de registros se utiliza para ver y actualizar registros a través de su conjunto de registros.  
  
-   Si selecciona **OLE DB** en **Tipo de cliente**, la clase de vista se derivará de [COleDBRecordView](../../mfc/reference/coledbrecordview-class.md) y se asociará a una clase derivada de [CTable](../../data/oledb/ctable-class.md) o [CCommand](../../data/oledb/ccommand-class.md).  
  
 **Tipo de cliente**  
 Indica si el proyecto utiliza clases OLE DB u ODBC.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**OLE DB**|Cuando esta opción está seleccionada, al hacer clic en el botón **Origen de datos** se invoca al asistente para **Propiedades de vínculo de datos**, que le ayudará a crear una conexión a un origen de datos OLE DB.|  
|**ODBC**|Cuando esta opción está seleccionada, al hacer clic en el botón **Origen de datos** se invoca al asistente para **Seleccionar origen de datos**, que le ayudará a crear una conexión a un origen de datos ODBC.|  
  
 **Origen de datos**  
 Haga clic en el botón **Origen de datos** para configurar un origen de datos mediante la base de datos y el controlador o proveedor especificados.  Si seleccionó OLE DB en la opción **Tipo de cliente**, este botón muestra el cuadro de diálogo **Propiedades de vínculo de datos**.  Si seleccionó ODBC en la opción **Tipo de cliente**, este botón muestra el cuadro de diálogo **Seleccionar origen de datos**.  Esta opción sólo está disponible si elige incluir una vista de base de datos en la aplicación.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Propiedades de vínculo de datos** \(OLE DB\)|Establece el origen de datos especificado mediante el proveedor OLE DB especificado.  Debe especificar el proveedor OLE DB, la ubicación de los datos, el origen de datos, el identificador de inicio de sesión y, opcionalmente, una contraseña.  Para ver más detalles acerca de este cuadro de diálogo, vea **Origen de datos** en [Asistente para consumidores OLE DB ATL](../../atl/reference/atl-ole-db-consumer-wizard.md).|  
|**Seleccionar origen de datos** \(ODBC\)|Establece el origen de datos especificado mediante el controlador ODBC especificado.  Debe seleccionar un nombre de origen de datos para elegir una tabla como origen de datos.  El asistente enlazará todas las columnas de la tabla a las variables miembro de una clase derivada de `CRecordset`.  Para ver más detalles acerca de este cuadro de diálogo, vea **Origen de datos** en [Asistente para consumidores ODBC MFC](../../mfc/reference/mfc-odbc-consumer-wizard.md).|  
  
> [!NOTE]
>  En versiones anteriores, al presionar la tecla MAYÚS y hacer clic en el botón **Origen de datos** se abría un cuadro de diálogo Abrir archivo en el que podía seleccionar un archivo de vínculo de datos \(.udl\).  Esta funcionalidad ya no se admite.  
  
 **Generar clase de base de datos con atributos**  
 Sólo está disponible para clientes OLE DB.  Especifica si las clases de base de datos del proyecto generado utilizan atributos.  
  
 **Enlazar todas las columnas**  
 Sólo está disponible para clientes ODBC.  Especifica si están enlazadas todas las columnas de la tabla seleccionada.  Si activa esta casilla, se enlazan todas las columnas; si no la activa, no se enlaza ninguna columna y deberá enlazarlas manualmente en la clase conjunto de registros.  
  
 **Tipo**  
 Sólo está disponible para clientes ODBC.  Especifica si el conjunto de registros es un de tipo dinámico o instantánea, como se indica en la tabla siguiente.  
  
|Opción|Descripción|  
|------------|-----------------|  
|**Conjunto de registros dinámicos**|Especifica que el conjunto de registros es de tipo dinámico.  Un conjunto de registros dinámico es el resultado de una consulta que proporciona una vista indizada de los datos de la base de datos consultada.  Sólo almacena en memoria caché un índice integral de los datos originales y, por tanto, ofrece una mejora de rendimiento con respecto a la instantánea.  El índice apunta directamente a cada registro encontrado como resultado de una consulta, e indica si se quita un registro.  También ofrece acceso a información actualizada en los registros consultados.|  
|Instantánea|Especifica que el conjunto de registros es una instantánea.  Una instantánea es el resultado de una consulta y es una vista de la base de datos en un momento determinado.  Todos los registros encontrados como resultado de la consulta se almacenan en memoria caché, por lo que no verá cambios en los registros originales.|  
  
## Vea también  
 [Asistente para aplicaciones MFC](../../mfc/reference/mfc-application-wizard.md)