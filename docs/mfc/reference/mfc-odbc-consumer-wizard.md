---
title: Asistente para consumidores ODBC MFC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 84fdc0d180f5b1b0f2e64c3597cb474611ad3914
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177436"
---
# <a name="mfc-odbc-consumer-wizard"></a>Asistente para consumidores ODBC MFC

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente configura una clase de conjunto de registros ODBC y los enlaces de datos necesarios para tener acceso al origen de datos especificado.

## <a name="uielement-list"></a>Lista de UIElement

- **Origen de datos**

  El botón **origen de datos** le permite configurar el origen de datos especificado mediante el controlador ODBC especificado. Para obtener más información acerca de los archivos de origen de datos (DSN), vea [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  El cuadro de diálogo **Seleccionar origen de datos** tiene dos pestañas:

  - Pestaña **origen de datos de archivo** :

     El cuadro **Buscar en** especifica el directorio en el que se van a seleccionar los archivos que se van a usar como orígenes de datos. El valor predeterminado es \Archivos de Programa\archivos Files\ODBC\Data sources. Los orígenes de datos de archivo (. DSN) existentes aparecen en el cuadro de lista principal. Puede configurar los orígenes de datos con anterioridad mediante la pestaña **DSN de archivo** del administrador de [orígenes de datos ODBC](/sql/odbc/admin/odbc-data-source-administrator), o bien crear otros nuevos mediante este cuadro de diálogo.

     Para crear un nuevo origen de datos de archivo desde este cuadro de `New` diálogo, haga clic en para especificar un nombre de DSN; aparecerá el cuadro de diálogo **crear nuevo origen de datos** . En el cuadro de diálogo **crear nuevo origen de datos** , seleccione un controlador adecuado `Next`y haga clic en **examinar**y seleccione el nombre del archivo que se va a usar como origen de datos (debe seleccionar "todos los archivos" para ver los archivos que no son DSN, como los archivos. xls); haga clic en y, a continuación, haga clic en **Finalizar.** `Next` (Si seleccionó un archivo que no es DSN, obtendrá un cuadro de diálogo específico del controlador, como "instalación de Microsoft Excel para ODBC", que convertirá el archivo en un DSN).

     > [!NOTE]
     > También puede crear un nuevo origen de datos de archivo con antelación mediante el administrador de orígenes de datos ODBC. En el menú **Inicio** , seleccione **configuración**, **Panel de control**, **herramientas administrativas**, **orígenes de datos (ODBC)** y, a continuación, **Administrador de orígenes de datos ODBC**.

     El cuadro **nombre de DSN** permite especificar un nombre para el origen de datos de archivo. Debe asegurarse de que el nombre de DSN termina con la extensión de archivo apropiada, como. xls para los archivos de Excel o. mdb para los archivos de acceso.

     Para obtener más información sobre los DSN, vea [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  - Pestaña **origen de datos** de la máquina:

     En esta pestaña se muestran los orígenes de datos del sistema y del usuario. Los orígenes de datos de usuario son específicos de un usuario de este equipo. Los orígenes de datos del sistema pueden ser utilizados por todos los usuarios de este equipo o en un servicio en todo el sistema. Ver [orígenes de datos](/sql/odbc/reference/machine-data-sources) de la máquina en el SDK de ODBC

     Para obtener más información sobre los orígenes de datos ODBC, vea [orígenes de datos](/sql/odbc/reference/data-sources) en el SDK de ODBC.

  Haga clic en **Aceptar** para terminar. Se muestra el cuadro de diálogo **Seleccionar objeto de base de datos**. En este cuadro de diálogo, seleccione la tabla o vista que usará el consumidor. Tenga en cuenta que puede seleccionar varias vistas y tablas manteniendo presionada la tecla control mientras hace clic en los elementos. Haga clic en **Aceptar** para terminar.

- **Clase**

      The name of the consumer class, based by default on the name of the file or machine data source that you selected.

- **Archivo .h**

   Nombre del archivo de encabezado de clase del consumidor, basado de forma predeterminada en el nombre del origen de datos del archivo o del equipo seleccionado.

- **Archivo .cpp**

   Nombre del archivo de implementación de clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o máquina seleccionado.

- **Type**

   Especifica si el conjunto de registros es Dynaset (valor predeterminado) o una instantánea.

   - Conjunto de **registros dinámico**: Especifica que el conjunto de registros es Dynaset. Un Dynaset es el resultado de una consulta que proporciona una vista indizada en los datos de la base de datos consultada. Un Dynaset almacena en caché solo un índice entero en los datos originales y, por tanto, ofrece una mejora en el rendimiento de una instantánea. El índice apunta directamente a cada registro encontrado como resultado de una consulta e indica si se quita un registro. También tiene acceso a la información actualizada en los registros consultados. Este es el valor predeterminado.

   - **Instantánea**: Especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros que se encuentran como resultado de la consulta se almacenan en caché, por lo que no ve ningún cambio en los registros originales.

- **Enlazar todas las columnas**

   Especifica si se enlazan todas las columnas de la tabla seleccionada. Si selecciona este cuadro (valor predeterminado), se enlazarán todas las columnas; Si no selecciona esta casilla, no se enlaza ninguna columna y debe enlazarla manualmente en la clase de conjunto de registros.

::: moniker-end

## <a name="see-also"></a>Vea también

[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
