---
title: Asistente para consumidores ODBC MFC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: fd7e8df6692889914af2dd060ac42ed4ca3ebb8b
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446407"
---
# <a name="mfc-odbc-consumer-wizard"></a>Asistente para consumidores ODBC MFC

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente configura una clase de conjunto de registros ODBC y los enlaces de datos necesarios para tener acceso al origen de datos especificado.

## <a name="uielement-list"></a>Lista de UIElement

- **Data Source** (Origen de datos)

  El botón **origen de datos** le permite configurar el origen de datos especificado mediante el controlador ODBC especificado. Para obtener más información acerca de los archivos de origen de datos (DSN), vea [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  El cuadro de diálogo **Seleccionar origen de datos** tiene dos pestañas:

  - Pestaña **origen de datos de archivo** :

     El cuadro **Buscar en** especifica el directorio en el que se van a seleccionar los archivos que se van a usar como orígenes de datos. El valor predeterminado es \Archivos de Programa\archivos Files\ODBC\Data sources. Los orígenes de datos de archivo (. DSN) existentes aparecen en el cuadro de lista principal. Puede configurar los orígenes de datos con anterioridad mediante la pestaña **DSN de archivo** del administrador de [orígenes de datos ODBC](/sql/odbc/admin/odbc-data-source-administrator), o bien crear otros nuevos mediante este cuadro de diálogo.

     Para crear un nuevo origen de datos de archivo desde este cuadro de diálogo, haga clic en `New` para especificar un nombre de DSN; aparecerá el cuadro de diálogo **crear nuevo origen de datos** . En el cuadro de diálogo **crear nuevo origen de datos** , seleccione un controlador adecuado y haga clic en `Next`; Haga clic en **examinar**y seleccione el nombre del archivo que se va a usar como origen de datos (tiene que seleccionar "todos los archivos" para ver los archivos que no son DSN, como los archivos. xls). Haga clic en `Next`y, a continuación, en **Finalizar**. (Si seleccionó un archivo que no es DSN, obtendrá un cuadro de diálogo específico del controlador, como "instalación de Microsoft Excel para ODBC", que convertirá el archivo en un DSN).

     > [!NOTE]
     > También puede crear un nuevo origen de datos de archivo con antelación mediante el administrador de orígenes de datos ODBC. En el menú **Inicio** , seleccione **configuración**, **Panel de control**, **herramientas administrativas**, **orígenes de datos (ODBC)** y, a continuación, **Administrador de orígenes de datos ODBC**.

     El cuadro **nombre de DSN** permite especificar un nombre para el origen de datos de archivo. Debe asegurarse de que el nombre de DSN termina con la extensión de archivo apropiada, como. xls para los archivos de Excel o. mdb para los archivos de acceso.

     Para obtener más información sobre los DSN, vea [orígenes de datos de archivo](/sql/odbc/reference/file-data-sources) en el SDK de ODBC.

  - Pestaña **origen de datos** de la máquina:

     En esta pestaña se muestran los orígenes de datos del sistema y del usuario. Los orígenes de datos de usuario son específicos de un usuario de este equipo. Los orígenes de datos del sistema pueden ser utilizados por todos los usuarios de este equipo o en un servicio en todo el sistema. Ver [orígenes de datos](/sql/odbc/reference/machine-data-sources) de la máquina en el SDK de ODBC

     Para obtener más información sobre los orígenes de datos ODBC, vea [orígenes de datos](/sql/odbc/reference/data-sources) en el SDK de ODBC.

  Haga clic en **Aceptar** para finalizar. Se muestra el cuadro de diálogo **Seleccionar objeto de base de datos**. En este cuadro de diálogo, seleccione la tabla o vista que usará el consumidor. Tenga en cuenta que puede seleccionar varias vistas y tablas manteniendo presionada la tecla control mientras hace clic en los elementos. Haga clic en **Aceptar** para finalizar.

- **Clase**

   El nombre de la clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o máquina seleccionado.

- **Archivo .h**

   Nombre del archivo de encabezado de clase del consumidor, basado de forma predeterminada en el nombre del origen de datos del archivo o del equipo seleccionado.

- **Archivo .cpp**

   Nombre del archivo de implementación de clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o máquina seleccionado.

- **Tipo**

   Especifica si el conjunto de registros es Dynaset (valor predeterminado) o una instantánea.

   - **Dynaset**: especifica que el conjunto de registros es Dynaset. Un Dynaset es el resultado de una consulta que proporciona una vista indizada en los datos de la base de datos consultada. Un Dynaset almacena en caché solo un índice entero en los datos originales y, por tanto, ofrece una mejora en el rendimiento de una instantánea. El índice apunta directamente a cada registro encontrado como resultado de una consulta e indica si se quita un registro. También tiene acceso a la información actualizada en los registros consultados. Este es el valor predeterminado.

   - **Snapshot**: especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros que se encuentran como resultado de la consulta se almacenan en caché, por lo que no ve ningún cambio en los registros originales.

- **Enlazar todas las columnas**

   Especifica si se enlazan todas las columnas de la tabla seleccionada. Si selecciona este cuadro (valor predeterminado), se enlazarán todas las columnas; Si no selecciona esta casilla, no se enlaza ninguna columna y debe enlazarla manualmente en la clase de conjunto de registros.

::: moniker-end

## <a name="see-also"></a>Consulte también

[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
