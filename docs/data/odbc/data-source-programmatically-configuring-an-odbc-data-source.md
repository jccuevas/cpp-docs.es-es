---
title: "Origen de datos: Configurar un origen de datos ODBC mediante programaci&#243;n | Microsoft Docs"
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
  - "SQLConfigDataSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "configurar orígenes de datos ODBC"
  - "conexiones ODBC, configurar"
  - "orígenes de datos ODBC, configurar"
  - "ejemplo del método SQLConfigDataSource"
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Origen de datos: Configurar un origen de datos ODBC mediante programaci&#243;n
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema explica cómo se pueden configurar nombres de orígenes de datos ODBC \(Conectividad abierta de bases de datos\) mediante programación.  Esto proporciona flexibilidad para tener acceso a los datos sin obligar al usuario a utilizar explícitamente el Administrador de ODBC u otros programas para especificar los nombres de los orígenes de datos.  
  
 Normalmente, un usuario ejecuta el Administrador ODBC para crear un origen de datos si el sistema de administración de bases de datos \(DBMS\) asociado admite esta operación.  
  
 Cuando se crea un origen de datos ODBC de Microsoft Access mediante el Administrador ODBC, se tienen dos opciones: seleccionar un archivo .mdb existente o crear uno nuevo.  No hay una forma de crear el archivo .mdb desde la aplicación ODBC de MFC mediante programación.  Por tanto, si la aplicación requiere que se coloquen datos en un origen de datos de Microsoft Access \(archivo .mdb\), lo más probable es que se desee tener un archivo .mdb vacío que se pueda utilizar o copiar cuando sea necesario.  
  
 De todos modos, muchos DBMS permiten la creación de orígenes de datos mediante programación.  Algunos orígenes de datos mantienen una especificación de directorio para las bases de datos.  Es decir, un directorio es el origen de datos y cada tabla del origen de datos se almacena en un archivo independiente \(en el caso de dBASE, cada tabla es un archivo .dbf\).  Los controladores para otras bases de datos ODBC, como Microsoft Access y SQL Server, requieren que se cumplan algunos criterios concretos para poder establecer un origen de datos.  Por ejemplo, cuando se utiliza el controlador ODBC de SQL Server se debe haber instalado SQL Server en un equipo.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> Ejemplo de SQLConfigDataSource  
 El siguiente ejemplo utiliza la función de la API de ODBC **::SQLConfigDataSource** para crear un nuevo origen de datos de Excel denominado "Nuevo origen de datos Excel":  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 Conviene señalar que el origen de datos es realmente un directorio \(C:\\EXCELDIR\); este directorio debe existir.  El controlador Excel utiliza directorios como orígenes de datos y archivos como tablas individuales \(una tabla por archivo .xls\).  
  
 Para obtener más información acerca de la creación de tablas, vea [Origen de datos: Crear una tabla en un origen de datos ODBC mediante programación](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
 La información siguiente explica los parámetros que hay que pasar a la función de la API de ODBC **::SQLConfigDataSource**.  Para utilizar **::SQLConfigDataSource**, se debe incluir el archivo de encabezado Odbcinst.h y utilizar la biblioteca de importación Odbcinst.lib.  Además, Odbccp32.dll debe estar en la ruta de acceso en tiempo de ejecución \(u Odbcinst.dll para 16 bits\).  
  
 Se puede crear un nombre de origen de datos ODBC mediante el Administrador ODBC o una herramienta similar.  Sin embargo, a veces es preferible crear un nombre de origen de datos directamente desde la aplicación para obtener acceso sin tener que pedir al usuario que ejecute una utilidad independiente.  
  
 El Administrador ODBC \(se suele instalar en el Panel de control\) crea un nuevo origen de datos insertando entradas en el Registro de Windows \(o, para 16 bits, en el archivo Odbc.ini\).  El Administrador de controladores ODBC consulta este archivo para obtener la información requerida sobre el origen de datos.  Es importante saber qué información hay que colocar en el Registro porque hay que proporcionarla con la llamada a **::SQLConfigDataSource**.  
  
 Aunque esta información se podría escribir directamente en el Registro sin utilizar **::SQLConfigDataSource**, las aplicaciones que lo hiciesen se estarían basando en la técnica actual que el Administrador de controladores utiliza para mantener los datos.  Si una revisión posterior del Administrador de controladores ODBC registrara la información sobre orígenes de datos de forma diferente, las aplicaciones que utilizasen esta técnica se interrumpirían.  En general, es aconsejable utilizar una función de la API cuando se proporcione.  Por ejemplo, el código se puede adaptar de 16 a 32 bits si se utiliza la función **::SQLConfigDataSource** , ya que la función escribe los datos correctamente en el archivo Odbc.ini o en el Registro.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> Parámetros de SQLConfigDataSource  
 A continuación se explican los parámetros de la función **::SQLConfigDataSource**.  La mayor parte de la información se ha tomado de la *Referencia del programador* de la API de ODBC que se proporciona con Visual C\+\+, versión 1.5 y posteriores.  
  
###  <a name="_core_function_prototype"></a> Prototipo de función  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### Comentarios  
  
####  <a name="_core_parameters_and_usage"></a> Parámetros y uso  
 *hwndParent*  
 Ventana especificada como propietaria de los cuadros de diálogo que el Administrador de controladores ODBC o el controlador ODBC específico crea para obtener información adicional del usuario sobre el nuevo origen de datos.  Si el parámetro `lpszAttributes` no proporciona suficiente información, aparece un cuadro de diálogo.  El parámetro *hwndParent* podría ser **NULL**.  
  
 `lpszDriver`  
 Descripción del controlador.  Éste es el nombre presentado a los usuarios en lugar del nombre de controlador físico \(la DLL\).  
  
 `lpszAttributes`  
 Lista de atributos en forma de "nombre de clave\=valor".  Estas cadenas están separadas por terminadores nulos con dos terminadores nulos consecutivos al final de la lista.  Estos atributos son principalmente entradas predeterminadas específicas del controlador, que se incluyen en el Registro para el nuevo origen de datos.  Una clave importante que no se menciona en la referencia de la API de ODBC para esta función es "DSN" \(*data source name*, nombre de origen de datos\), que especifica el nombre del nuevo origen de datos.  El resto de las entradas son específicas del controlador para el nuevo origen de datos.  Con frecuencia, no es necesario proporcionar todas las entradas, ya que el controlador puede solicitar del usuario los nuevos valores mediante cuadros de diálogo. Se ha de establecer *hwndParent* en **NULL** para que esto se produzca. Se pueden proporcionar explícitamente valores predeterminados para que no se soliciten valores al usuario.  
  
###### A fin de determinar la descripción de un controlador para el parámetro lpszDriver mediante el Administrador ODBC  
  
1.  Ejecute el Administrador de ODBC.  
  
2.  Haga clic en **Agregar**.  
  
 Se proporciona una lista de los controladores instalados y sus descripciones.  Utilice esta descripción como parámetro `lpszDriver`.  Observe que se utiliza la descripción completa, como, por ejemplo, "Archivos Excel \(\*.xls\)", en la que se incluyen la extensión del nombre de archivo y los paréntesis si aparecen en la descripción.  
  
 Como alternativa, puede examinar el Registro \(o, para 16 bits, el archivo Odbcinst.ini\), que contiene una lista de todas las entradas y descripciones de los controladores bajo la clave del Registro "ODBC Drivers" \(o la sección \[ODBC Drivers\] en Odbcinst.ini\).  
  
 Una forma de encontrar los nombres de clave y valores para el parámetro `lpszAttributes` es examinar el archivo Odbc.ini para un origen de datos que ya esté configurado \(por ejemplo, uno que se haya configurado por el Administrador ODBC\).  
  
###### Para encontrar nombres de clave y valores para el parámetro lpszAttributes  
  
1.  Ejecute el editor del Registro de Windows \(o, para 16 bits, abra el archivo Odbc.ini\).  
  
2.  Busque la información sobre orígenes de datos ODBC utilizando uno de los siguientes métodos:  
  
    -   Para 32 bits, busque la clave **HKEY\_CURRENT\_USER\\Software\\ODBC\\ODBC.INI\\ODBC Data Sources** en el panel izquierdo.  
  
         El panel de la derecha enumera las entradas de la forma: pub: REG\_SZ:*\<nombre de origen de datos\>*", en las que *\<nombre de origen de datos\>* es un origen de datos que ya ha sido configurado con los valores deseados para el controlador que se pretende utilizar.  Seleccione el origen de datos que desee, por ejemplo, SQL Server.  Los elementos que siguen a la cadena "pub:" son, por este orden, el nombre de clave y el valor que se van a utilizar en el parámetro `lpszAttributes`.  
  
    -   Para 16 bits, busque la sección del archivo Odbc.ini marcada por \[*\<nombre de origen de datos\>*\].  
  
         Las líneas que siguen a esta línea tendrán la forma "nombre de clave\=valor".  Estas son exactamente las entradas que hay que utilizar en el parámetro `lpszAttributes`.  
  
 También puede que desee examinar la documentación para el controlador específico que va a utilizar.  Puede encontrar información útil en la Ayuda en pantalla correspondiente al controlador, a la que se puede tener acceso ejecutando el Administrador ODBC.  Estos archivos de Ayuda se suelen colocar en el directorio WINDOWS\\SYSTEM de Windows NT, Windows 3.1 o Windows 95.  
  
###### Para obtener ayuda en pantalla del controlador ODBC  
  
1.  Ejecute el Administrador de ODBC.  
  
2.  Haga clic en **Agregar**.  
  
3.  Seleccione el nombre del controlador.  
  
4.  Haga clic en **Aceptar**.  
  
 Cuando el Administrador de ODBC muestre la información para crear un nuevo origen de datos para ese controlador concreto, haga clic en **Ayuda**.  Se abrirá el archivo de Ayuda para dicho controlador que, por lo general, contiene información importante sobre el uso del controlador.  
  
## Vea también  
 [Origen de datos \(ODBC\)](../../data/odbc/data-source-odbc.md)