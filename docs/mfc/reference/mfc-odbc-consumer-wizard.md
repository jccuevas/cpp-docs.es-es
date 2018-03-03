---
title: Asistente para consumidores ODBC MFC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.class.mfc.consumer.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC ODBC Consumer Wizard
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ad9e4aeb15d2af04987883b6554d569e3cc16b8d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-odbc-consumer-wizard"></a>Asistente para consumidores ODBC MFC
Inserte aquí "Búsqueda de resumen de los resultados".  
  
 Este asistente configura una clase de conjunto de registros ODBC y los enlaces de datos necesario para tener acceso al origen de datos especificado.  
  
## <a name="uielement-list"></a>Lista de UIElement  
 **Origen de datos**  
 El **origen de datos** botón permite configurar el origen de datos especificado mediante el controlador ODBC especificado. Para obtener más información sobre los archivos de origen de datos (DSN), consulte [orígenes de datos de archivo](https://msdn.microsoft.com/library/ms715401.aspx) en el SDK de ODBC. El **Seleccionar origen de datos** cuadro de diálogo tiene dos pestañas:  
  
-   **Origen de datos de archivo** ficha: el **buscar en** cuadro especifica el directorio en el que se va a seleccionar los archivos que se usará como orígenes de datos. El valor predeterminado es \Program Files\Common Files\ODBC\Data Sources. Los orígenes de datos de archivo existente (archivos .dsn) aparecen en el cuadro de lista principal. Puede configurar los orígenes de datos antes de tiempo mediante la **DSN de archivo** pestaña en el [Administrador de orígenes de datos ODBC](https://msdn.microsoft.com/library/ms714024.aspx), o crear otros nuevos mediante este cuadro de diálogo.  
  
     Para crear un nuevo origen de datos de archivo desde este cuadro de diálogo, haga clic en `New` para especificar un nombre DSN; la **Create New Data Source** aparece el cuadro de diálogo. En el **Create New Data Source** diálogo cuadro, seleccione un controlador apropiado y haga clic en `Next`; haga clic en **examinar**y seleccione el nombre del archivo que se usará como un origen de datos (tiene que seleccionar "Todos los archivos" en ver archivos no DSN, como los archivos .xls); Haga clic en `Next`y, a continuación, haga clic en **finalizar**. (Si ha seleccionado un archivo no DSN, obtendrá un cuadro de diálogo específico del controlador, como "ODBC Microsoft Excel Setup", lo que convertirá el archivo a un DSN.)  
  
    > [!NOTE]
    >  También puede crear un nuevo origen de datos de archivo con antelación mediante el Administrador de orígenes de datos ODBC. Desde el **iniciar** menú, seleccione **configuración**, **el Panel de Control**, **herramientas administrativas**, **deorígenesdedatos(ODBC)**y, a continuación, **Administrador de orígenes de datos ODBC**.  
  
     El **nombre DSN** cuadro le permite especificar un nombre para el origen de datos de archivo. Debe asegurarse de que el nombre DSN termina con la extensión de archivo adecuado, como .xls para archivos de Excel o .mdb para acceder a los archivos.  
  
     Para obtener más información acerca de DNS, consulte [orígenes de datos de archivo](https://msdn.microsoft.com/library/ms715401.aspx) en el SDK de ODBC.  
  
-   **La máquina de origen de datos** ficha: esta pestaña muestra orígenes de datos de usuario y sistema. Orígenes de datos de usuario son específicos de un usuario en este equipo. Orígenes de datos del sistema pueden usarse por todos los usuarios en este equipo o en un servicio de todo el sistema. Vea [equipo orígenes de datos](https://msdn.microsoft.com/library/ms710952.aspx) en el SDK de ODBC  
  
 Para obtener más información sobre orígenes de datos ODBC, vea [orígenes de datos](https://msdn.microsoft.com/library/ms711688.aspx) en el SDK de ODBC.  
  
 Haga clic en **Aceptar** para finalizar. El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo. En este cuadro de diálogo, seleccione la tabla o ver que el consumidor usará. Tenga en cuenta que puede seleccionar varias vistas y tablas manteniendo presionada la tecla control mientras hace clic en los elementos.  
  
 **Clase**  
 El nombre de la clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o una máquina que ha seleccionado.  
  
 **archivo .h**  
 El nombre del archivo de encabezado de clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o una máquina que ha seleccionado.  
  
 **archivo .cpp**  
 El nombre del archivo de implementación de clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o una máquina que ha seleccionado.  
  
 **Type**  
 Especifica si el conjunto de registros es un conjunto de registros dinámicos (valor predeterminado) o una instantánea.  
  
-   **Conjunto de registros dinámicos**: Especifica que el conjunto de registros es un conjunto de registros dinámicos. Un conjunto de registros dinámicos es el resultado de una consulta que proporciona una vista indizada en datos la base de consultada. Un conjunto de registros dinámicos se almacena en memoria caché solo un índice entero a los datos originales y, por tanto, ofrece un rendimiento obtener a través de una instantánea. El índice apunta directamente a cada registro encontrados como resultado de una consulta y se indica si se elimina un registro. También tienen acceso a la información actualizada en los registros consultados. Este es el valor predeterminado.  
  
-   **Instantánea**: Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un punto en el tiempo. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá los cambios realizados en los registros originales.  
  
 **Enlazar todas las columnas**  
 Especifica si se enlazan todas las columnas de la tabla seleccionada. Si se activa esta casilla (predeterminado), se enlazan todas las columnas; Si no activa esta casilla, se enlaza ninguna columna y deberá enlazarlas manualmente en la clase de conjunto de registros.  
  
## <a name="see-also"></a>Vea también  
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)

