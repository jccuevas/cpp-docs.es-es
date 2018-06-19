---
title: Crear un consumidor sencillo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumers, creating
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 711aaaff2bc4e012ba4c4ef78465f06c51b9d307
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33098529"
---
# <a name="creating-a-simple-consumer"></a>Crear un consumidor sencillo
Use el Asistente para proyectos ATL y el Asistente para consumidores OLE DB ATL para generar un consumidor de plantillas OLE DB.  
  
#### <a name="to-create-a-console-application-for-an-ole-db-consumer"></a>Para crear una aplicación de consola para un consumidor OLE DB  
  
1.  En el menú **Archivo** , haga clic en **Nuevo**y, a continuación, haga clic en **Proyecto**.  
  
     Aparecerá el cuadro de diálogo **Nuevo proyecto** .  
  
2.  En el panel tipos de proyecto, haga clic en el **proyectos de Visual C++** carpeta y, a continuación, haga clic en el **proyecto Win32** icono en el panel Plantillas. En el **nombre** cuadro, escriba el nombre del proyecto, por ejemplo, **MyCons**.  
  
3.  Haga clic en **Aceptar**.  
  
     Aparece el Asistente para proyectos Win32.  
  
4.  En el **configuración de la aplicación** página, seleccione **aplicación de consola**y, a continuación, seleccione **agregar compatibilidad con ATL**.  
  
5.  Haga clic en **finalizar** para cerrar el asistente y generar el proyecto.  
  
 A continuación, use el Asistente para consumidores OLE DB ATL para agregar un objeto de consumidor OLE DB.  
  
#### <a name="to-create-a-consumer-with-the-atl-ole-db-consumer-wizard"></a>Para crear un consumidor con el Asistente para consumidores OLE DB ATL  
  
1.  En la vista de clases, haga clic en el `MyCons` proyecto.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
     El **Agregar clase** aparece el cuadro de diálogo.  
  
3.  En el panel de categorías, haga clic en **Visual C++**, haga clic en el **consumidores OLE DB ATL** icono en el panel de plantillas y, a continuación, haga clic en **abiertos**.  
  
     Aparece el Asistente para consumidores OLE DB ATL.  
  
4.  Haga clic en el **origen de datos** botón.  
  
     El **propiedades de vínculo de datos** aparece el cuadro de diálogo.  
  
5.  En el **propiedades de vínculo de datos** diálogo cuadro, realice lo siguiente:  
  
    -   En el **proveedor** ficha, especifique un proveedor OLE DB.  
  
    -   En el **conexión** ficha, especifique el nombre del servidor, el Id. de inicio de sesión y la contraseña para el origen de datos y la base de datos en el servidor.  
  
    > [!NOTE]
    >  Hay un problema de seguridad con la **Permitir guardar contraseña** característica de la **propiedades de vínculo de datos** cuadro de diálogo. En **especificar información para iniciar sesión en el servidor**, hay dos botones de radio: **la seguridad integrada de Windows NT de uso** y **utilizar un nombre de usuario específico y una contraseña**.  
  
    > [!NOTE]
    >  Si selecciona **utilizar un nombre de usuario específico y una contraseña**, tiene la opción de guardar la contraseña (mediante la **Permitir guardar contraseña** casilla de verificación); sin embargo, esta opción no es segura. Se recomienda que seleccione **la seguridad integrada de Windows NT de uso**; esta opción utiliza Windows NT para verificar tu identidad.  
  
    > [!NOTE]
    >  Si no puede usar la seguridad integrada de Windows NT, debe usar una aplicación de nivel medio para solicitar al usuario la contraseña o para almacenar la contraseña en una ubicación con mecanismos de seguridad para proteger la red (en lugar de en el código fuente).  
  
     Después de seleccionar el proveedor y otras opciones, haga clic en **Probar conexión** para comprobar las selecciones realizadas en las páginas de cuadro de diálogo anterior. Si el **resultados** cuadro informes `Test connection succeeded`, haga clic en **Aceptar** para crear el vínculo de datos.  
  
     El **seleccionar un objeto de base de datos** aparece el cuadro de diálogo.  
  
6.  Utilice el control de árbol para seleccionar una tabla, vista o procedimiento almacenado. Con el fin de este procedimiento, seleccione la tabla Products de la base de datos Northwind.  
  
7.  Haga clic en **Aceptar**. Esto le devuelve al Asistente para consumidores OLE DB ATL.  
  
8.  Complete el asistente los nombres de `Class` y **archivo .h** basado en el nombre de la tabla, vista o procedimiento almacenado que seleccionó. Puede editar estos nombres si quiere.  
  
9. Desactive el **atributos** casilla de verificación para que el asistente crea el código de consumidor mediante [clases de plantilla OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) en lugar del predeterminado [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. En **tipo**, seleccione **comando**.  
  
     El asistente crea un [CCommand](../../data/oledb/ccommand-class.md)-consumidor basado en si selecciona **comando** o un [CTable](../../data/oledb/ctable-class.md)-consumidor basado en si selecciona **tabla**. La clase de tabla o el comando se denomina después el objeto seleccionado, pero puede modificar el nombre.  
  
11. En **compatibilidad**, deje el **cambio**, **insertar**, y **eliminar** casillas desactivadas.  
  
     Seleccione el **cambio**, **insertar**, y **eliminar** casillas de verificación para poder modificar, insertar y eliminar los registros del conjunto de filas, del si es necesario. Para obtener más información acerca de cómo escribir datos a los datos de almacén, consulte [actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).  
  
12. Haga clic en **finalizar** para crear el consumidor.  
  
 El asistente genera una clase de comando y una clase de registro de usuario, como se muestra en [clases generadas](../../data/oledb/consumer-wizard-generated-classes.md). La clase de comando tendrá el nombre que escribió en el `Class` cuadro del asistente (en este caso, `CProducts`), y la clase de registro de usuario tendrá un nombre de la forma "*ClassName*descriptor de acceso" (en este caso, `CProductsAccessor`).  
  
> [!NOTE]
>  El asistente coloca la línea siguiente en Products.h:  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Esta línea evita que la aplicación de consumidor se compile y le recuerda que compruebe la cadena de conexión para las contraseñas codificadas de forma rígida. Después de comprobar la cadena de conexión, puede quitar esta línea de código.  
  
## <a name="see-also"></a>Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)