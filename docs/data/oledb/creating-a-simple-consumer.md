---
title: Crear un consumidor sencillo
ms.date: 11/06/2018
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
ms.openlocfilehash: 060a39a8436ff73900ebfaea7d1c882b9862ee7e
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59025142"
---
# <a name="creating-a-simple-consumer"></a>Crear un consumidor sencillo

Use la **Asistente para proyectos ATL** y **el Asistente para consumidores OLE DB ATL** para generar un consumidor de plantillas OLE DB.

## <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Para crear una aplicación de consola para un consumidor OLE DB

1. En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.

   Aparecerá el cuadro de diálogo **Nuevo proyecto** .

1. En el **tipos de proyecto** panel, haga clic en el **instalado** > **Visual C++** > **Windows Desktop** carpeta, y, a continuación, haga clic en el **Asistente de escritorio de Windows** icono en el **plantillas** panel. En el **nombre** , escriba el nombre del proyecto, por ejemplo, *MyCons*.

1. Haga clic en **Aceptar**.

   El **proyecto de escritorio de Windows** aparece el asistente.

1. En el **configuración de la aplicación** página, seleccione **aplicación de consola**y, a continuación, seleccione **agregar archivos de encabezado comunes para ATL**.

1. Haga clic en **Aceptar** para cerrar el asistente y generar el proyecto.

A continuación, use el **el Asistente para consumidores OLE DB ATL** para agregar un objeto de consumidor OLE DB.

## <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Para crear un consumidor con el Asistente para consumidores OLE DB ATL

1. En **el Explorador de soluciones**, haga clic en el `MyCons` proyecto.

1. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **nuevo elemento**.

   Aparecerá el cuadro de diálogo **Agregar nuevo elemento**.

1. En el **categorías** panel, haga clic en **instalado** > **Visual C++** > **ATL**, haga clic en el **ATL OLEDB Consumer** icono en el **plantillas** panel y, a continuación, haga clic en **agregar**.

   El **Asistente para consumidores OLE DB de ATL** aparece.

1. Haga clic en el **origen de datos** botón.

   El **propiedades de vínculo de datos** aparece el cuadro de diálogo.

1. En el **propiedades de vínculo de datos** diálogo cuadro, realice lo siguiente:

   1. En el **proveedor** ficha, especifique un proveedor OLE DB.

   1. En el **conexión** ficha, especifique la información necesaria, como nombre del servidor, Id. de inicio de sesión y contraseña para el origen de datos y la base de datos en el servidor.

      > [!NOTE]
      > Hay un problema de seguridad con el **Permitir guardar contraseña** característica de la **propiedades de vínculo de datos** cuadro de diálogo. En **especificar información para iniciar sesión en el servidor**, hay dos botones de radio: **La seguridad integrada de Windows NT de uso** y **utilizar un nombre de usuario específico y una contraseña**.

      > [!NOTE]
      > Si selecciona **utilizar un nombre de usuario específico y una contraseña**, tiene la opción de guardar la contraseña (mediante la **Permitir guardar contraseña** casilla de verificación); sin embargo, esta opción no es segura. Se recomienda que seleccione **seguridad integrada de uso Windows NT**; esta opción utiliza Windows NT para verificar tu identidad.

      > [!NOTE]
      > Si no puede usar seguridad integrada de Windows NT, debe usar una aplicación de nivel intermedio para preguntar al usuario la contraseña o para almacenar la contraseña en una ubicación con mecanismos de seguridad para proteger la red (en lugar de en el código fuente).

   1. Después de seleccionar el proveedor y otras opciones, haga clic en **Probar conexión** para comprobar las selecciones realizadas en las páginas de cuadro de diálogo anterior. Si el **resultados** cuadro informes `Test connection succeeded`, haga clic en **Aceptar** para crear el vínculo de datos.

   El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo.

1. Utilice el control de árbol para seleccionar una tabla, vista o procedimiento almacenado. En este ejemplo, seleccione el `Products` tabla desde el `Northwind` base de datos.

1. Haga clic en **Aceptar**. Esto le devuelve a la **el Asistente para consumidores OLE DB ATL**.

1. El asistente rellena los nombres de `Class` y **archivo .h** según el nombre de la tabla, vista o procedimiento almacenado que seleccionó. Puede modificar estos nombres si lo desea.

1. Desactive el **atributos** casilla de verificación para que el asistente crea el código de consumidor con [clases de plantilla OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) en lugar del predeterminado [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md).

1. En **tipo**, seleccione **comando**.

   El asistente crea un [CCommand](../../data/oledb/ccommand-class.md)-consumidor basado en si selecciona **comando** o un [CTable](../../data/oledb/ctable-class.md)-consumidor basado en si selecciona **tabla**. La clase de tabla o comando se denomina después del objeto seleccionado, pero puede modificar el nombre.

1. En **soporte**, deje el **cambio**, **insertar**, y **eliminar** casillas desactivadas.

   Seleccione el **cambio**, **insertar**, y **eliminar** casillas de verificación para admitir el cambio, insertar y eliminar los registros del conjunto de filas del. Para obtener más información sobre cómo escribir datos a los datos de almacén, consulte [actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).

1. Haga clic en **finalizar** para crear el consumidor.

El asistente genera una clase de comando y una clase de registro de usuario, como se muestra en [clases generadas](../../data/oledb/consumer-wizard-generated-classes.md). La clase de comando tendrá el nombre que escribió en el `Class` cuadro en el Asistente (en este caso, `CProducts`), y la clase de registro de usuario tendrá un nombre con el formato "*ClassName*descriptor de acceso" (en este caso, `CProductsAccessor`).

> [!NOTE]
> El asistente coloca la línea siguiente en `Products.h`:

```cpp
#error Security Issue: The connection string may contain a password
```

> [!NOTE]
> Esta línea evita que la aplicación de consumidor de compilar y le recuerda que compruebe la cadena de conexión para las contraseñas codificadas de forma rígida. Después de comprobar la cadena de conexión, puede quitar esta línea de código.

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)
