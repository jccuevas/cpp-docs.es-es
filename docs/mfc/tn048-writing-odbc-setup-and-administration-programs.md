---
title: "TN048: Escribir programas de instalaci&#243;n y administraci&#243;n de ODBC para aplicaciones de base de datos MFC | Microsoft Docs"
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
  - "vc.mfc.odbc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "instalar ODBC"
  - "MFC, aplicaciones de base de datos"
  - "ODBC, y MFC"
  - "ODBC, instalar"
  - "configurar, programas de instalación ODBC"
  - "TN048"
ms.assetid: d456cdd4-0513-4a51-80c0-9132b66115ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN048: Escribir programas de instalaci&#243;n y administraci&#243;n de ODBC para aplicaciones de base de datos MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

> [!NOTE]
>  La nota técnica siguiente no se ha actualizado desde que se incluyó por primera vez en la documentación en línea.  Como resultado, algunos procedimientos y temas podrían estar obsoletos o ser incorrectos.  Para obtener información más reciente, se recomienda buscar el tema de interés en el índice de la documentación en línea.  
  
 Las aplicaciones utilizar clases de base de datos MFC necesitarán un programa de instalación que instale los componentes de ODBC.  También pueden necesitar un programa de ODBC Administración que recuperar información sobre los controladores disponibles, para especificar controladores predeterminados y configurar orígenes de datos.  Esta nota describe el uso del instalador de la API de ODBC de escribir estos programas.  
  
##  <a name="_mfcnotes_writing_an_odbc_setup_program"></a> Escribir un programa de instalación de ODBC  
 Una aplicación de base de datos de MFC requiere el administrador de controladores ODBC \(ODBC.DLL\) y controladores ODBC poder obtener los orígenes de datos.  Muchos controladores ODBC también requieren archivos DLL adicionales de la red y la comunicación.  La mayoría de los controladores ODBC incluidos en un programa de instalación que instale los componentes necesarios de ODBC.  Los programadores de aplicaciones mediante clases de base de datos MFC pueden:  
  
-   Confíe en los programas de instalación controlador\- específicos para instalar componentes de ODBC.  Esto no requieren ningún otro trabajo en la parte del desarrollador — simplemente puede redistribuir el programa de instalación del controlador.  
  
-   O bien, puede escribir dispone del programa de instalación, que instalará el administrador de controladores y el controlador.  
  
 El instalador de la API de ODBC se puede utilizar para escribir programas de instalación específicos de la aplicación.  Las funciones del instalador API se implementan en el instalador DLL — ODBCINST.DLL en Windows de 16 bits y ODB CCP32 .DLL de ODBC en Win32.  Una aplicación puede llamar a **SQLInstallODBC** en el instalador DLL, que instalará el administrador de controladores ODBC, los controladores ODBC, y cualquier traductor requerido.  A continuación de los controladores instalados y los traductores en el archivo de ODBCINST.INI \(o el registro, en NT\).  **SQLInstallODBC** requiere la ruta completa del archivo de ODBC.INF, que contiene la lista de controladores que se instalan y se describen los archivos que componen cada controlador.  También contiene información similar sobre el administrador y los traductores de controlador.  Los archivos de ODBC.INF proporciona normalmente para los desarrolladores de controlador.  
  
 Un programa puede instalar también los componentes individuales de ODBC.  Para instalar el administrador de controladores, primero llama a **SQLInstallDriverManager** de un programa en el instalador DLL para obtener el directorio de destino para el administrador de controladores.  Normalmente es el directorio en el que los archivos DLL de Windows residen.  El programa utilice la información en la sección \[el administrador de controladores ODBC\] del archivo de ODBC.INF para copiar el administrador de controladores y archivos relacionados del disco de instalación a este directorio.  Para instalar un controlador individual, primero llama a **SQLInstallDriver** de un programa en el instalador DLL para agregar la especificación de controlador en el archivo de ODBCINST.INI \(o al registro, en NT\).  **SQLInstallDriver** devuelve el directorio de destino del controlador que tienen el directorio en el que los archivos DLL de Windows residen.  El programa utilice la información en la sección del controlador del archivo de ODBC.INF para copiar el controlador DLL y archivos relacionados del disco de instalación a este directorio.  
  
 Para obtener más información sobre ODBC.INF, ODBCINST.INI y utilizar el instalador API, vea *la referencia del programador* de ODBC en el CD capítulo 19, para instalar el software de ODBC.  
  
##  <a name="_mfcnotes_writing_an_odbc_administrator"></a> Escribir un administrador de ODBC  
 Una aplicación de base de datos de MFC puede instalar y configurar orígenes de datos ODBC de dos maneras, como sigue:  
  
-   Utilice el administrador de ODBC \(disponible como programa o como elemento del Panel de control\).  
  
-   Cree poseen el programa para configurar orígenes de datos.  
  
 Un programa que configurar orígenes de datos realiza llamadas de función al instalador DLL.  El instalador DLL llama una DLL de instalación para configurar un origen de datos.  Hay una DLL de instalación para cada controlador; puede ser el controlador el archivo DLL, o un archivo DLL independiente.  La DLL de instalación pide al usuario la información que el controlador necesita para conectarse al origen de datos y el traductor predeterminado, si se admite.  Llama al instalador DLL y API de Windows para registrar esta información en el archivo de ODBC.INI \(o el registro\).  
  
 Para mostrar un cuadro de diálogo con el que un usuario puede agregar, modificar, y eliminar orígenes de datos, llamadas **SQLManageDataSources** de un programa en el instalador DLL.  Se llama a esta función cuando el instalador DLL se realiza desde el Panel de control.  Para agregar, modificar, o eliminar un origen de datos, **SQLManageDataSources** llama **ConfigDSN** en la DLL de instalación para el controlador asociado a ese origen de datos.  Para agregar directamente, modificar, o eliminar orígenes de datos, un programa llama a **SQLConfigDataSource** en el instalador DLL.  El programa pasa el nombre del origen de datos y una opción que especifica la acción que se va a realizar.  **SQLConfigDataSource** llama **ConfigDSN** en la DLL de instalación y lo pasa los argumentos de **SQLConfigDataSource**.  
  
 Para obtener más información, vea *la referencia del progarmador* de ODBC en el CD el capítulo 23, la referencia de función DLL de instalación, y el capítulo 24, referencia de función DLL del instalador.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)