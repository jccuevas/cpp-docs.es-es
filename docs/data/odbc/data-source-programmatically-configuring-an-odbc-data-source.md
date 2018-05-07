---
title: 'Origen de datos: Configurar mediante programación un origen de datos ODBC | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: conceptual
f1_keywords:
- SQLConfigDataSource
dev_langs:
- C++
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e1f46ad566874d80b45593e7aecfeee2d5d88841
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Origen de datos: Configurar un origen de datos ODBC mediante programación
Este tema explica cómo configurar nombres de origen de datos Open Database Connectivity (ODBC) mediante programación. Esto le da flexibilidad para acceder a los datos sin obligar al usuario a utilizar explícitamente el Administrador de ODBC u otros programas para especificar los nombres de orígenes de datos.  
  
 Normalmente, un usuario ejecuta el Administrador de ODBC para crear un origen de datos si el sistema de administración de asociados de la base de datos (DBMS) es compatible con esta operación.  
  
 Al crear un origen de datos ODBC de Microsoft Access a través del Administrador de ODBC, tendrá dos opciones: puede seleccionar un archivo .mdb existente o puede crear un nuevo archivo .mdb. No hay ningún mecanismo de programación de crear el archivo .mdb desde la aplicación ODBC de MFC. Por lo tanto, si la aplicación requiere que se coloquen datos en un origen de datos de Microsoft Access (archivo .mdb), lo más probable es que desee tener un archivo .mdb vacío que se puede utilizar o copiar siempre que lo necesite.  
  
 Sin embargo, muchos DBMS permiten la creación del origen de datos mediante programación. Algunos orígenes de datos mantienen una especificación de directorio para las bases de datos. Es decir, un directorio es el origen de datos y cada tabla del origen de datos se almacena en un archivo independiente (en el caso de dBASE, cada tabla es un archivo .dbf). Controladores para otras bases de datos ODBC, como Microsoft Access y SQL Server, requieren que se cumplan algunos criterios concretos para poder establecer un origen de datos. Por ejemplo, cuando se usa el controlador ODBC de SQL Server, debe haber establecido un equipo con SQL Server.  
  
##  <a name="_core_sqlconfigdatasource_example"></a> Ejemplo de SQLConfigDataSource  
 En el ejemplo siguiente se usa el **:: SQLConfigDataSource** función de la API de ODBC para crear un nuevo origen de datos de Excel denominado nuevo origen de datos de Excel:  
  
```  
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",   
                   "DSN=New Excel Data Source\0"   
                   "Description=New Excel Data Source\0"   
                   "FileType=Excel\0"   
                   "DataDirectory=C:\\EXCELDIR\0"   
                   "MaxScanRows=20\0");  
```  
  
 Tenga en cuenta que el origen de datos es realmente un directorio (C:\EXCELDIR); Este directorio debe existir. El controlador de Excel utiliza directorios como orígenes de datos y archivos como las tablas individuales (una tabla por cada archivo .xls).  
  
 Para obtener más información acerca de cómo crear tablas, vea [origen de datos: crear una tabla en un origen de datos ODBC mediante programación](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).  
  
 La siguiente información describe los parámetros que deben pasarse a la **:: SQLConfigDataSource** función de la API de ODBC. Usar **:: SQLConfigDataSource**, debe incluir el archivo de encabezado Odbcinst.h y usar el archivo de importación Odbcinst.lib. Además, Odbccp32.dll debe estar en la ruta de acceso en tiempo de ejecución (u Odbcinst.dll para 16 bits).  
  
 Puede crear un nombre de origen de datos ODBC mediante el Administrador de ODBC o una utilidad similar. Sin embargo, a veces es conveniente crear un nombre de origen de datos directamente desde la aplicación para obtener acceso sin requerir al usuario que ejecute una utilidad independiente.  
  
 El Administrador de ODBC (normalmente se instala en el Panel de Control) crea un nuevo origen de datos insertando entradas en el registro de Windows (o, para 16 bits, en el archivo Odbc.ini). El Administrador de controladores ODBC consulta este archivo para obtener la información necesaria sobre el origen de datos. Es importante saber qué información debe colocarse en el registro porque hay que proporcionarla con la llamada a **:: SQLConfigDataSource**.  
  
 Aunque esta información podría escribirse directamente en el registro sin usar **:: SQLConfigDataSource**, cualquier aplicación que lo haga depende de la técnica actual que el Administrador de controladores utiliza para mantener sus datos. Si una revisión posterior del Administrador de controladores ODBC registrara sobre orígenes de datos de forma diferente, cualquier aplicación que use esta técnica se interrumpe. Es normalmente se recomienda usar una función de API cuando se proporciona uno. Por ejemplo, el código es portabilidad de 16 bits a 32 bits si usas el **:: SQLConfigDataSource** funciona, ya que la función se escribe correctamente en el archivo Odbc.ini o en el registro.  
  
##  <a name="_core_sqlconfigdatasource_parameters"></a> Parámetros de SQLConfigDataSource  
 Los siguientes explican los parámetros de la **:: SQLConfigDataSource** función. Gran parte de la información se obtiene de la API de ODBC *referencia del programador* suministrados con Visual C++ versión 1.5 y posteriores.  
  
###  <a name="_core_function_prototype"></a> Prototipo de función  
  
```  
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);  
```  
  
### <a name="remarks"></a>Comentarios  
  
####  <a name="_core_parameters_and_usage"></a> Parámetros y uso  
 *hwndParent*  
 La ventana especificada como propietario de los cuadros de diálogo que el Administrador de controladores ODBC o el controlador ODBC específico crea para obtener información adicional del usuario sobre el nuevo origen de datos. Si el `lpszAttributes` parámetro no proporciona suficiente información, aparece un cuadro de diálogo. El *hwndParent* parámetro podría ser **NULL**.  
  
 `lpszDriver`  
 Descripción del controlador. Este es el nombre que se presentan a los usuarios en lugar de con el nombre de controlador físico (la DLL).  
  
 `lpszAttributes`  
 Lista de atributos con el formato "nombre de clave = valor". Estas cadenas se separan mediante terminadores null con dos terminadores null consecutivos al final de la lista. Estos atributos son principalmente entradas de específicas del controlador de forma predeterminada, que se incluyen en el registro para el nuevo origen de datos. Una clave importante que no se menciona en la referencia de API de ODBC para esta función es "DSN" ("nombre origen de datos"), que especifica el nombre del nuevo origen de datos. El resto de las entradas son específicas para el controlador para el nuevo origen de datos. A menudo no es necesario proporcionar todas las entradas porque el controlador puede solicitar al usuario con cuadros de diálogo para los nuevos valores. (Establecer *hwndParent* a **NULL** para hacer esto.) Puede proporcionar explícitamente los valores predeterminados para que no se pide al usuario.  
  
###### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Para determinar la descripción de un controlador para el parámetro lpszDriver mediante el Administrador de ODBC  
  
1.  Ejecute el Administrador de ODBC.  
  
2.  Haga clic en **Agregar**.  
  
 Esto proporciona una lista de controladores instalados y sus descripciones. Utilice esta descripción como el `lpszDriver` parámetro. Tenga en cuenta que utiliza la descripción completa, como "Archivos de Excel (*.xls)", que se incluyen la extensión de nombre de archivo y los paréntesis si existen en la descripción.  
  
 Como alternativa, puede examinar el registro (o, para 16 bits, el archivo Odbcinst.ini), que contiene una lista de todas las entradas de controlador y las descripciones en la clave del registro "ODBC Drivers" (o la sección [ODBC Drivers] en Odbcinst.ini).  
  
 Una manera de buscar los nombres de clave y valores para el `lpszAttributes` parámetro consiste en Examinar el archivo Odbc.ini para un origen de datos ya configurados (por ejemplo, uno que se ha configurado por el Administrador de ODBC).  
  
###### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Para buscar nombres de clave y valores para el parámetro lpszAttributes  
  
1.  Ejecutar el editor del registro de Windows (o, para 16 bits, abra el archivo Odbc.ini).  
  
2.  Buscar la información de orígenes de datos ODBC mediante uno de los siguientes:  
  
    -   Para 32 bits, busque la clave **HKEY_CURRENT_USER\Software\ODBC\ODBC. INI\ODBC Data Sources** en el panel izquierdo.  
  
         El panel derecho muestran las entradas de la forma: "pub: REG_SZ:*<data source name>*", donde *<data source name>* es un origen de datos que ya se ha configurado con las opciones que desee para el controlador piensa Para usar. Seleccione el origen de datos que desee, por ejemplo, SQL Server. Los elementos que siguen a la cadena "pub:" son, en orden, keyname y valor para usar en su `lpszAttributes` parámetro.  
  
    -   Para 16 bits, busque la sección en el archivo Odbc.ini marcada por [*\<el nombre del origen de datos >*].  
  
         Las líneas que siguen a esta línea tienen el formato "nombre de clave = valor". Estos son exactamente las entradas que se van a usar en su `lpszAttributes` parámetro.  
  
 También puede examinar la documentación para el controlador específico que se va a usar. Puede encontrar información útil en la Ayuda en pantalla para el controlador, que se puede acceder mediante la ejecución de administrador de ODBC. Normalmente, estos archivos de ayuda se colocan en el directorio WINDOWS\SYSTEM para Windows NT, Windows 3.1 o Windows 95.  
  
###### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Para obtener ayuda en línea para el controlador ODBC  
  
1.  Ejecute el Administrador de ODBC.  
  
2.  Haga clic en **Agregar**.  
  
3.  Seleccione el nombre del controlador.  
  
4.  Haga clic en **Aceptar**.  
  
 Cuando el Administrador de ODBC muestre la información para crear un nuevo origen de datos para ese controlador concreto, haga clic en **ayuda**. Se abrirá el archivo de ayuda para ese controlador concreto, que normalmente contiene información importante sobre el uso del controlador.  
  
## <a name="see-also"></a>Vea también  
 [Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)