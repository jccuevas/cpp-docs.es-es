---
title: Crear un consumidor sencillo
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: f72363478696baccb0473e37104427b1516b39c3
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524999"
---
# <a name="creating-a-simple-consumer"></a>Crear un consumidor sencillo

::: moniker range="vs-2019"

El Asistente para consumidores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores. Puede seguir agregando la funcionalidad manualmente. Para obtener más información, consulte [Crear un consumidor sin utilizar un asistente](creating-a-consumer-without-using-a-wizard.md).

::: moniker-end

::: moniker range="vs-2017"

Use el **Asistente para proyectos ATL** y **el Asistente para consumidores OLE DB ATL** con el fin de generar un consumidor de plantillas OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Crear una aplicación de consola para un consumidor OLE DB

1. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

1. En el panel **Tipos de proyecto**, haga clic en la carpeta **Instalado** > **Visual C++** > **Windows Desktop** y, a continuación, haga clic en el icono de **Asistente para escritorio de Windows** en el panel **plantillas**. En el cuadro **Nombre**, escriba el nombre del proyecto, por ejemplo, *MiCons*.

1. Haga clic en **Aceptar**.

   Se muestra el asistente **Proyecto de escritorio de Windows**.

1. En la página **Configuración de la aplicación**, seleccione **Aplicación de consola** y, a continuación, seleccione **Agregar archivos de encabezado comunes para ATL**.

1. Haga clic en **Aceptar** para cerrar el asistente y generar el proyecto.

A continuación, use el **Asistente para consumidores OLE DB ATL** con el fin de agregar un objeto de consumidor OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Para crear un consumidor con el Asistente para consumidores OLE DB ATL

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto `MyCons`.

1. En el menú contextual, elija **Agregar** y después haga clic en **Nuevo elemento**.

   Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

1. En el panel **Categorías**, haga clic en **Instalado** > **Visual C++** > **ATL**, en el icono de **Consumidor OLEDB ATL** del panel **Plantillas** y, a continuación, haga clic en **Agregar**.

   Se muestra el **Asistente para consumidores OLEDB ATL**.

1. Haga clic en el botón **Origen de datos**.

   Aparece un nuevo cuadro de diálogo **Propiedades de vínculo de datos**.

1. En el cuadro de diálogo **Propiedades de vínculo de datos**, realice lo siguiente:

   1. En la pestaña **Proveedor**, especifique un proveedor OLE DB.

   1. En la pestaña **Conexión**, especifique la información necesaria, como el nombre del servidor, el identificador de inicio de sesión y la contraseña del origen de datos y la base de datos en el servidor.

      > [!NOTE]
      > Hay un problema de seguridad con la característica de **permitir la guardar contraseña** del cuadro de diálogo **Propiedades de vínculo de datos**. En **Especificar información para iniciar sesión en el servidor**, hay dos botones de radio: **Usar seguridad integrada de Windows N** y **Usar un nombre de usuario y contraseña específicos**.

      > [!NOTE]
      > Si selecciona **Usar un nombre de usuario y contraseña específicos**, tiene la opción de guardar la contraseña (mediante la casilla de verificación para **Permitir guardar contraseña**); sin embargo, esta opción no es segura. Se recomienda que seleccione **Usar seguridad integrada de Windows NT**; esta opción usa Windows NT para comprobar la identidad.

      > [!NOTE]
      > Si no puede usar la seguridad integrada de Windows NT, debe usar una aplicación de nivel intermedio para preguntar al usuario la contraseña o para almacenar la contraseña en una ubicación con mecanismos de seguridad para protegerla (en lugar de en el código fuente).

   1. Después de seleccionar el proveedor y otras opciones, haga clic en **Probar conexión** para comprobar las selecciones realizadas en las páginas de cuadro de diálogo anterior. Si el cuadro **Resultados** notifica `Test connection succeeded`, haga clic en **Aceptar** para crear el vínculo de datos.

   Se muestra el cuadro de diálogo **Seleccionar objeto de base de datos**.

1. Utilice el control de árbol para seleccionar una tabla, una vista o procedimiento almacenado. En este ejemplo, seleccione la tabla `Products` desde la base de datos `Northwind`.

1. Haga clic en **Aceptar**. Esta acción devuelve al usuario al **Asistente para consumidores OLE DB ATL**.

1. El asistente rellena los nombres de `Class` y el archivo **.h** según el nombre de la tabla, la vista o el procedimiento almacenado que seleccionó. Puede editar estos nombres si lo desea.

1. Desactive la casilla de verificación **Atributos** para que el asistente cree el código de consumidor con [clases de plantilla OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) en lugar de los [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md) predeterminados.

1. En **Tipo**, seleccione **Command**.

   El asistente crea un consumidor basado en [CCommand](../../data/oledb/ccommand-class.md) en si selecciona un consumidor basado en **Command** o [CTable](../../data/oledb/ctable-class.md) si selecciona **Tabla**. La clase de tabla o comando se denomina después del objeto seleccionado, pero puede modificar el nombre.

1. En **Soporte técnico**, deje los cuadros **Cambiar**, **Insertar** y **Eliminar** vacíos.

   Seleccione las casillas de verificación **Cambiar**, **Insertar** y **Eliminar** para admitir el cambio, la inserción y la eliminación de los registros del conjunto de filas. Para obtener más información sobre cómo escribir datos a los datos de almacén, consulte [Actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).

1. Haga clic en **Finalizar** para crear el consumidor.

El asistente genera una clase de comando y una clase de registro de usuario, tal cual se muestra en [Clases generadas por el Asistente para consumidores](../../data/oledb/consumer-wizard-generated-classes.md). La clase de comando tendrá el nombre que escriba en el cuadro `Class` del asistente (por ejemplo, `CProducts`) y la clase de registro de usuario tendrá un nombre con el formato "*ClassName*Accessor" (por ejemplo, `CProductsAccessor`).

> [!NOTE]
> El asistente coloca la línea siguiente en `Products.h`:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Esta línea evita que la aplicación de consumidor compile y le recuerda que compruebe la cadena de conexión para las contraseñas codificadas de forma rígida. Después de comprobar la cadena de conexión, puede quitar esta línea de código.

::: moniker-end

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
