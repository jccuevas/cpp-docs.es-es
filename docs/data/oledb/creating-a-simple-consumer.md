---
title: "Crear un consumidor sencillo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "consumidores OLE DB, crear"
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear un consumidor sencillo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Para generar un consumidor de las plantillas OLE DB, utilice el Asistente para proyectos ATL y el Asistente para consumidores OLE DB ATL.  
  
#### Para crear una aplicación de consola para un consumidor OLE DB  
  
1.  En el menú **Archivo**, haga clic en **Nuevo** y, a continuación, haga clic en **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto**.  
  
2.  En el panel Tipos de proyecto, haga clic en la carpeta **Proyectos de Visual C\+\+** y, en el panel Plantillas, haga clic en el icono **Proyecto Win32**.  En el cuadro **Nombre**, escriba el nombre del proyecto, por ejemplo, **MyCons**.  
  
3.  Haga clic en **Aceptar**.  
  
     Aparecerá el Asistente para proyectos Win32.  
  
4.  En la página **Configuración de la aplicación**, seleccione **Aplicación de consola** y seleccione **Agregar compatibilidad con ATL**.  
  
5.  Haga clic en **Finalizar** para cerrar el asistente y generar el proyecto.  
  
 A continuación, use el Asistente para consumidores OLE DB ATL para agregar un objeto de consumidor OLE DB.  
  
#### Para crear un consumidor mediante el Asistente para consumidores OLE DB ATL  
  
1.  En la vista de clases, haga clic con el botón secundario en el proyecto de `MyCons` .  
  
2.  En el menú contextual, haga clic en **Agregar** y, a continuación, en **Agregar clase**.  
  
     Aparecerá el cuadro de diálogo **Agregar clase**.  
  
3.  En el panel Categorías, haga clic en **Visual C\+\+**, en el panel Plantillas, haga clic en el icono **Consumidor OLE DB ATL** y, finalmente, haga clic en **Abrir**.  
  
     Se abre el Asistente para consumidores OLE DB ATL.  
  
4.  Haga clic en el botón **Origen de datos**.  
  
     Aparece el cuadro de diálogo **Propiedades de vínculo de datos**.  
  
5.  En el cuadro de diálogo **Propiedades de vínculo de datos**, haga lo siguiente:  
  
    -   En la ficha **Proveedor**, especifique un proveedor OLE DB.  
  
    -   En la ficha **Conexión**, especifique el nombre del servidor, el identificador de inicio de sesión y la contraseña para conectar con el origen de datos y la base de datos del servidor.  
  
    > [!NOTE]
    >  Existe un problema de seguridad con la característica **Permitir guardar contraseña** del cuadro de diálogo **Propiedades de vínculo de datos**.  En **Especificar información para iniciar sesión en el servidor**, hay dos botones de radio: **Usar seguridad integrada de Windows NT** y **Usar un nombre de usuario y una contraseña específicos**.  
  
    > [!NOTE]
    >  Si selecciona **Usar un nombre de usuario y una contraseña específicos**, tiene la opción de guardar la contraseña \(por medio de la casilla **Permitir guardar contraseña**\); no obstante, ésta es una opción poco segura.  Se recomienda seleccionar **Usar seguridad integrada de Windows NT**, ya que utiliza Windows NT para comprobar la identidad.  
  
    > [!NOTE]
    >  Si no puede utilizar la seguridad integrada de Windows NT, debe usar una aplicación de nivel medio para solicitar al usuario una contraseña o para almacenar la contraseña en una ubicación con mecanismos de seguridad a fin de poder protegerla, en lugar de en el código fuente.  
  
     Después de seleccionar el proveedor y las demás opciones, haga clic en **Probar conexión** para comprobar las opciones seleccionadas en las fichas anteriores del cuadro de diálogo.  Si los informes `Test connection succeeded`, haga clic en **Aceptar** del cuadro de **Resultados** para crear el vínculo de datos.  
  
     Se abrirá el cuadro de diálogo **Seleccionar objeto de base de datos**.  
  
6.  Use el control de árbol para seleccionar una tabla, vista o procedimiento almacenado.  Para los fines de este procedimiento, seleccione la tabla Productos de la base de datos Northwind.  
  
7.  Haga clic en **Aceptar**.  Con ello regresará al Asistente para consumidores OLE DB ATL.  
  
8.  El asistente completa los nombres de `Class` y **.h file** basándose en el nombre de la tabla, vista, o procedimiento almacenado que seleccionó.  Estos nombres se pueden modificar si se desea.  
  
9. Desactive la casilla **Con atributos** para que el asistente cree el código del consumidor mediante [clases de plantilla OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md) en lugar de utilizar la opción predeterminada de [atributos de consumidor OLE DB](../../windows/ole-db-consumer-attributes.md).  
  
10. En **Tipo**, seleccione **Comando**.  
  
     El asistente crea un consumidor basado en [CCommand](../../data/oledb/ccommand-class.md) si se activa **Comando**, o un consumidor basado en [CTable](../../data/oledb/ctable-class.md) si se activa **Tabla**.  La clase de tabla o comando recibe el nombre del objeto seleccionado, pero se puede cambiar.  
  
11. En **Compatibilidad**, deje desactivadas las casillas **Cambiar**, **Insertar** y **Eliminar**.  
  
     Active las casillas **Cambiar**, **Insertar**, y **Eliminar** para poder modificar, insertar y eliminar los registros del conjunto de filas, si así se requiere.  Para obtener más información sobre cómo escribir datos en el almacén de datos, vea [Actualizar conjuntos de filas](../../data/oledb/updating-rowsets.md).  
  
12. Haga clic en **Finalizar** para crear el consumidor.  
  
 El asistente genera una clase de comando y una clase de registro de usuario, como se muestra en [Clases generadas por el asistente para consumidores](../../data/oledb/consumer-wizard-generated-classes.md).  La clase de comando tendrá el nombre que escribió en el cuadro de `Class` del asistente \(en este caso, `CProducts`\), y la clase de registro de usuario tendrá un nombre con el formato “*ClassNameAccessor*” \(en este caso, `CProductsAccessor`\).  
  
> [!NOTE]
>  El asistente coloca la línea siguiente en Products.h:  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  Esta línea evita que la aplicación de consumidor se compile y le recuerda que compruebe las contraseñas incluidas en el código de la cadena de conexión.  Después de comprobar la cadena de conexión, puede quitar esta línea de código.  
  
## Vea también  
 [Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)