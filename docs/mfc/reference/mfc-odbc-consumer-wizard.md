---
title: "Asistente para consumidores ODBC MFC | Microsoft Docs"
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
  - "vc.codewiz.class.mfc.consumer.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para consumidores ODBC MFC"
  - "asistentes [MFC]"
ms.assetid: f64a890b-a252-4887-88a1-782a7cd4ff3d
caps.latest.revision: 7
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Asistente para consumidores ODBC MFC
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Insertar aquí el resumen de "Resultados de la búsqueda".  
  
 Este asistente configura una clase de conjunto de registros de ODBC y los enlaces de datos necesarios para el acceso al origen de datos especificado.  
  
## Lista de UIElement  
 **Origen de datos**  
 El botón **Origen de datos** permite configurar el origen de datos especificado mediante el controlador de ODBC especificado.  Para obtener más información acerca de los archivos de código fuente de datos \(DSN\), vea el artículo [Archivos de origen de datos \(ODBC\)](https://msdn.microsoft.com/en-us/library/ms715401.aspx) en el SDK de ODBC.  El cuadro de diálogo **Seleccionar origen de datos** tiene dos fichas:  
  
-   Ficha **Origen de datos de archivo**: el cuadro **Buscar en** especifica el directorio donde puede seleccionar los archivos que desee usar como orígenes de datos.  El valor predeterminado es \\Archivos de programa\\Archivos comunes\\ODBC\\Data Sources.  Los archivos de origen de datos ya existentes \(archivos .dsn\) aparecen en el cuadro de lista principal.  Puede configurar los orígenes de datos por adelantado, en la ficha **DSN de archivo** del [Administrador de orígenes de datos ODBC](https://msdn.microsoft.com/en-us/library/ms714024.aspx) o crear orígenes nuevos en este cuadro de diálogo.  
  
     Para crear un origen de datos de archivo nuevo en este cuadro de diálogo, haga clic en `New` y especifique un nombre de DSN; se abre el cuadro de diálogo **Crear nuevo origen de datos**.  En este cuadro de diálogo, seleccione un controlador apropiado y haga clic en `Next`; haga clic en **Examinar** y seleccione el nombre del archivo que desee usar como origen de datos \(seleccione "Todos los archivos" si desea ver los archivos no DSN, como los archivos .xls\); haga clic en `Next` y por último en **Finalizar**. \(Si selecciona un archivo no DSN, se abrirá un cuadro de diálogo específico del controlador, como "ODBC Microsoft Excel Setup", que convierte el archivo en DSN.\)  
  
    > [!NOTE]
    >  También puede crear un origen de datos de archivo nuevo de antemano por medio del Administrador de orígenes de datos ODBC.  En el menú **Inicio**, seleccione **Configuración**, **Panel de control**, **Herramientas administrativas**, **Orígenes de datos \(ODBC\)** y, después, **Administrador de orígenes de datos ODBC**.  
  
     En el cuadro **Nombre de DSN** puede especificar un nombre para el origen de datos de archivo.  Asegúrese de que el nombre de DSN termina en la extensión de archivo apropiada, como .xls para archivos Excel o .mdb para archivos Access.  
  
     Para obtener más información acerca de DNS, vea [Orígenes de datos de archivo](https://msdn.microsoft.com/en-us/library/ms715401.aspx) en el SDK de ODBC.  
  
-   Ficha **Origen de datos de equipo**: esta ficha muestra orígenes de datos de sistema y de usuario.  Los orígenes de datos de usuario son específicos de un usuario de este equipo.  Los orígenes de datos del sistema pueden ser utilizados por todos los usuarios de este equipo en un servicio global del sistema.  Vea [Orígenes de datos de equipo](https://msdn.microsoft.com/en-us/library/ms710952.aspx) en el SDK de ODBC.  
  
 Para obtener más información acerca de los orígenes de datos ODBC, vea [Orígenes de datos](https://msdn.microsoft.com/en-us/library/ms711688.aspx) en el SDK de ODBC.  
  
 Para terminar, haga clic en **Aceptar**.  Se abrirá el cuadro de diálogo **Seleccionar objeto de base de datos**.  En este cuadro de diálogo, seleccione la tabla o la vista que deba usar el consumidor.  Tenga en cuenta que puede seleccionar varias vistas y tablas, si mantiene presionada la tecla de control a la vez que hace clic en los elementos.  
  
 **Clase**  
 El nombre de la clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o equipo seleccionado.  
  
 **Archivo .h**  
 El nombre del archivo de encabezado de la clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o equipo seleccionado.  
  
 **Archivo .cpp**  
 El nombre del archivo de implementación de la clase de consumidor, basado de forma predeterminada en el nombre del origen de datos de archivo o equipo seleccionado.  
  
 **Tipo**  
 Especifica si el conjunto de registros es de tipo dinámico \(el valor predeterminado\) o una instantánea.  
  
-   **Dinámico**: especifica que el conjunto de registros es de tipo dinámico.  Un conjunto de registros dinámico es el resultado de una consulta que proporciona una vista indizada de los datos de la base de datos consultada.  Sólo almacena en memoria caché un índice integral de los datos originales y, por tanto, ofrece una mejora de rendimiento con respecto a la instantánea.  El índice apunta directamente a cada registro encontrado como resultado de una consulta, e indica si se quita un registro.  También ofrece acceso a información actualizada en los registros consultados.  Éste es el valor predeterminado.  
  
-   **Instantánea**: especifica que el conjunto de registros es una instantánea.  Una instantánea es el resultado de una consulta y es una vista de la base de datos en un momento determinado.  Todos los registros encontrados como resultado de la consulta se almacenan en memoria caché, por lo que no verá cambios en los registros originales.  
  
 **Enlazar todas las columnas**  
 Especifica si están enlazadas todas las columnas de la tabla seleccionada.  Si activa esta casilla \(el valor predeterminado\), se enlazan todas las columnas; si no la activa, no se enlaza ninguna columna y deberá enlazarlas manualmente en la clase conjunto de registros.  
  
## Vea también  
 [Consumidor ODBC de MFC](../../mfc/reference/adding-an-mfc-odbc-consumer.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)