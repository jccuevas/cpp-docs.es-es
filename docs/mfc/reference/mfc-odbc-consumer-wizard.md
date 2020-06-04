---
title: Asistente para consumidores ODBC MFC
ms.date: 08/29/2019
helpviewer_keywords:
- wizards [MFC]
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
ms.openlocfilehash: 45087434c0093f99383096761d58a8029c9d5009
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373018"
---
# <a name="mfc-odbc-consumer-wizard"></a>Asistente para consumidores ODBC MFC

::: moniker range="vs-2019"

Este asistente no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Este asistente configura una clase de conjunto de registros ODBC y los enlaces de datos necesarios para tener acceso al origen de datos especificado.

## <a name="uielement-list"></a>Lista de UIElement

- **Fuente de datos**

  El botón **Origen** de datos permite configurar el origen de datos especificado mediante el controlador ODBC especificado. Para obtener más información acerca de los archivos de origen de datos (DSN), vea [Orígenes de datos](/sql/odbc/reference/file-data-sources) de archivo en el SDK de ODBC.

  El cuadro de diálogo **Seleccionar origen** de datos tiene dos pestañas:

  - **Ficha Origen de datos** de archivo:

     El cuadro **Buscar en** especifica el directorio en el que se seleccionan los archivos que se utilizarán como orígenes de datos. El valor predeterminado es "Archivos de programa", "Archivos comunes", ODBC y orígenes de datos. Los orígenes de datos de archivo existentes (archivos .dsn) aparecen en el cuadro de lista principal. Puede configurar los orígenes de datos con antelación mediante la ficha **DSN** de archivo en el Administrador de orígenes de [datos ODBC](/sql/odbc/admin/odbc-data-source-administrator)o crear otros nuevos mediante este cuadro de diálogo.

     Para crear un nuevo origen de datos `New` de archivo a partir de este cuadro de diálogo, haga clic para especificar un nombre DSN; aparece el cuadro de diálogo Crear nuevo origen de **datos.** En el cuadro de diálogo Crear nuevo origen `Next`de **datos,** seleccione un controlador adecuado y haga clic en ; Haga clic en **Examinar**y seleccione el nombre del archivo que se utilizará como origen de datos (debe seleccionar "Todos los archivos" para ver los archivos que no son DSN, como los archivos .xls); haga `Next`clic en , y, a continuación, haga clic en **Finalizar**. (Si seleccionó un archivo que no es DSN, obtendrá un cuadro de diálogo específico del controlador, como "Configuración de ODBC Microsoft Excel", que convertirá el archivo en un DSN.)

     > [!NOTE]
     > También puede crear un nuevo origen de datos de archivo de antemano mediante el Administrador de orígenes de datos ODBC. En el menú **Inicio** , seleccione **Configuración**, Panel de **control**, **Herramientas administrativas**, Orígenes de datos **(ODBC)** y, a continuación, **Administrador de orígenes**de datos ODBC .

     El cuadro **Nombre DSN** le permite especificar un nombre para el origen de datos de archivo. Debe asegurarse de que el nombre DSN termina con la extensión de archivo adecuada, como .xls para archivos de Excel o .mdb para archivos de Access.

     Para obtener más información sobre DSN, vea [Orígenes de datos](/sql/odbc/reference/file-data-sources) de archivo en el SDK de ODBC.

  - **Ficha Origen de datos** de la máquina:

     Esta pestaña enumera las fuentes del sistema y de los datos de usuario. Los orígenes de datos de usuario son específicos de un usuario en esta máquina. Los orígenes de datos del sistema pueden ser utilizados por todos los usuarios en esta máquina o en un servicio de todo el sistema. Consulte [Orígenes de datos](/sql/odbc/reference/machine-data-sources) de máquina en el SDK de ODBC

     Para obtener más información sobre orígenes de datos ODBC, vea [Orígenes de datos](/sql/odbc/reference/data-sources) en el SDK de ODBC.

  Haz clic en **Aceptar** para finalizar. Se muestra el cuadro de diálogo **Seleccionar objeto de base de datos**. En este cuadro de diálogo, seleccione la tabla o vista que usará el consumidor. Tenga en cuenta que puede seleccionar varias vistas y tablas manteniendo pulsada la tecla de control mientras hace clic en los elementos. Haz clic en **Aceptar** para finalizar.

- **Clase**

   El nombre de la clase consumidora, basado de forma predeterminada en el nombre del archivo o origen de datos del equipo que seleccionó.

- **Archivo .h**

   El nombre del archivo de encabezado de clase de consumidor, basado de forma predeterminada en el nombre del archivo o origen de datos del equipo que seleccionó.

- **Archivo .cpp**

   El nombre del archivo de implementación de la clase de consumidor, basado de forma predeterminada en el nombre del archivo o origen de datos del equipo que seleccionó.

- **Tipo**

   Especifica si el conjunto de registros es un conjunto de registros dinámicos (valor predeterminado) o una instantánea.

  - **Dynaset**: especifica que el conjunto de registros es un conjunto de registros dinámicos. Un conjunto de registros dinámicos es el resultado de una consulta que proporciona una vista indizada en los datos de la base de datos consultada. Un conjunto de registros dinámicos almacena en caché solo un índice integral de los datos originales y, por lo tanto, ofrece una ganancia de rendimiento sobre una instantánea. El índice apunta directamente a cada registro encontrado como resultado de una consulta e indica si se quita un registro. También tiene acceso a información actualizada en los registros consultados. Este es el valor predeterminado.

  - **Instantánea:** especifica que el conjunto de registros es una instantánea. Una instantánea es el resultado de una consulta y es una vista en una base de datos en un momento dado. Todos los registros encontrados como resultado de la consulta se almacenan en caché, por lo que no verá ningún cambio en los registros originales.

- **Enlazar todas las columnas**

   Especifica si todas las columnas de la tabla seleccionada están enlazadas. Si selecciona este cuadro (predeterminado), todas las columnas están enlazadas; si no selecciona este cuadro, no se enlaza ninguna columna y debe enlazarlas manualmente en la clase de conjunto de registros.

::: moniker-end

## <a name="see-also"></a>Consulte también

[Consumidor ODBC MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)<br/>
[Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)
