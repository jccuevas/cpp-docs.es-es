---
title: "Utilizar el enlace de datos de ADO en Visual C++ | Microsoft Docs"
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
  - "ADO [C++], enlace de datos"
  - "controles enlazados [C++], ADO"
  - "controles enlazados [C++], RDO"
  - "enlace de datos [C++], ADO"
  - "enlace de datos [C++], RDO"
ms.assetid: ad193919-3437-41ee-b41c-9d353f6274e5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar el enlace de datos de ADO en Visual C++
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El uso del enlace de datos de ADO en Visual C\+\+ requiere los pasos siguientes:  
  
-   Agregar un control de datos ADO.  
  
-   Apuntar a un origen de datos.  
  
-   Especificar el origen de registros \(mediante una consulta SQL o un lenguaje de recuperación de datos\).  
  
-   Agregar un control enlazado a datos de ADO.  
  
-   Conectar el control enlazado a datos a un control de datos ADO.  
  
-   Seleccionar los campos que desea enlazar al origen de registros del control de datos ADO.  
  
### Para utilizar el enlace de datos de ADO en Visual C\+\+  
  
1.  Cree un aplicación basada en cuadros de diálogo MFC o una aplicación de vista de formulario de MFC mediante el Asistente para aplicaciones MFC.  
  
2.  Agregue el control de datos de Microsoft ADO al cuadro de diálogo; vea [Insertar el control en una aplicación de Visual C\+\+](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md).  
  
3.  Haga que el control de datos ADO apunte al origen de datos OLE DB.  
  
    1.  Haga clic con el botón secundario en el control de datos de ADO y, a continuación, haga clic en **Propiedades**.  
  
    2.  En la ficha **Control**, haga clic en **Usar cadena de conexión**.  Puede utilizar el proveedor suministrado o eliminarlo.  
  
    3.  Haga clic en **Compilar**.  Si eliminó el proveedor de **Usar cadena de conexión**, ya puede definir uno.  Después de definir el proveedor, obtenga acceso de nuevo a las propiedades del control de datos ADO y vuelva a seleccionar **Compilar** para continuar.  
  
         Si hay un proveedor definido en **Usar cadena de conexión** antes de seleccionar **Compilar**, ahora puede definir las propiedades de vínculo de datos.  Esto muestra el Asistente para vínculos de datos.  
  
    4.  Cambie el valor de **Proveedor** si es necesario y defina los valores adecuados de **Ubicación** y **Origen de datos** para el proveedor.  Por ejemplo, si utiliza un proveedor de SQL Server, el valor de **Ubicación** especifica el servidor de bases de datos y el valor de **Origen de datos** especifica la base de datos.  Si utiliza un proveedor ODBC, el valor de **Origen de datos** corresponde al DSN ODBC.  
  
    5.  Haga clic en la ficha **Autenticación** y establezca los valores de **Nombre de usuario** y **Contraseña**, si lo requiere el origen de datos.  
  
    6.  Haga clic en la ficha **Conexión** y después en **Probar conexión** para probar el origen de datos.  Desplácese al final de la Ventana de salida para ver si se superó la prueba.  Si no se superó debe comprobar la configuración del origen de datos.  Algunos errores comunes son contraseñas no válidas o valores incorrectos de los campos **Ubicación** y **Origen de datos**.  
  
    7.  Salga del Asistente para vínculos de datos y vuelva a la hoja de propiedades del control de datos ADO.  
  
4.  En la ficha `RecordSource`, escriba una consulta en **Texto del comando \(SQL\)**.  Los controles enlazados a datos pueden enlazarse a los resultados de esta consulta.  La consulta suele ser SQL.  Sin embargo, algunos proveedores OLE DB no utilizan SQL.  
  
5.  Establezca los valores de las propiedades del control de datos ADO que desee establecer y cierre la hoja de propiedades del control de datos ADO.  
  
6.  Agregue un control enlazado a datos.  Por ejemplo, agregue el control DataGrid, que es diferente del control DBGrid de RDO.  
  
7.  Establezca las propiedades del control DataGrid.  
  
    1.  Haga clic con el botón secundario en la cuadrícula de datos y, a continuación, haga clic en **Propiedades**.  
  
    2.  Haga clic en la ficha **Todas** y luego establezca el valor de la propiedad **DataSource** en el control de datos ADO.  Haga clic en la lista desplegable **DataSource** y busque el identificador del control de datos ADO.  El nombre de identificador predeterminado es IDC\_ADODC1.  
  
8.  Para ejecutar en modo de prueba, presione CTRL\+T.  Puede desplazarse por los datos.  Presione la tecla ESC o cierre el cuadro de diálogo para finalizar el modo de prueba.  
  
 Si compila y ejecuta el programa, también se puede desplazar por los datos.  
  
## Vea también  
 [Enlace de datos de ADO](../../data/ado-rdo/ado-databinding.md)   
 [Enlace de datos con controles ActiveX en Visual C\+\+](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)