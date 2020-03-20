---
title: 'Origen de datos: Configurar un origen de datos ODBC mediante programación'
ms.date: 11/04/2016
f1_keywords:
- SQLConfigDataSource
helpviewer_keywords:
- ODBC data sources, configuring
- SQLConfigDataSource method example
- ODBC connections, configuring
- configuring ODBC data sources
ms.assetid: b8cabe9b-9e12-4d73-ae36-7cb12dee3213
ms.openlocfilehash: 38f0f383256a05c983fb7e7d7a498e16881c7b78
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545964"
---
# <a name="data-source-programmatically-configuring-an-odbc-data-source"></a>Origen de datos: Configurar un origen de datos ODBC mediante programación

En este tema se explica cómo puede configurar los nombres de orígenes de datos de conectividad abierta de bases de datos (ODBC) mediante programación. Esto le ofrece flexibilidad para tener acceso a los datos sin obligar al usuario a usar explícitamente el administrador de ODBC u otros programas para especificar los nombres de los orígenes de datos.

Normalmente, un usuario ejecuta el administrador de ODBC para crear un origen de datos si el sistema de administración de bases de datos (DBMS) asociado es compatible con esta operación.

Al crear un origen de datos ODBC de Microsoft Access a través del administrador de ODBC, se le proporcionan dos opciones: puede seleccionar un archivo. mdb existente o puede crear un nuevo archivo. mdb. No hay ninguna manera de crear el archivo. mdb a partir de la aplicación ODBC de MFC mediante programación. Por lo tanto, si la aplicación requiere la colocación de datos en un origen de datos de Microsoft Access (archivo. mdb), lo más probable es que desee tener un archivo. mdb vacío que pueda usar o copiar siempre que lo necesite.

Sin embargo, muchos DBMS permiten la creación de orígenes de datos mediante programación. Algunos orígenes de datos mantienen una especificación de directorio para las bases de datos. Es decir, un directorio es el origen de datos y cada tabla del origen de datos se almacena en un archivo independiente (en el caso de dBASE, cada tabla es un archivo. dbf). Los controladores de otras bases de datos ODBC, como Microsoft Access y SQL Server, requieren que se satisfagan determinados criterios para poder establecer un origen de datos. Por ejemplo, al usar el controlador ODBC de SQL Server, debe haber establecido un equipo SQL Server.

##  <a name="sqlconfigdatasource-example"></a><a name="_core_sqlconfigdatasource_example"></a>Ejemplo de SQLConfigDataSource

En el ejemplo siguiente se usa la función de la API de ODBC `::SQLConfigDataSource` para crear un nuevo origen de datos de Excel denominado nuevo origen de datos de Excel:

```
SQLConfigDataSource(NULL,ODBC_ADD_DSN, "Excel Files (*.xls)",
                   "DSN=New Excel Data Source\0"
                   "Description=New Excel Data Source\0"
                   "FileType=Excel\0"
                   "DataDirectory=C:\\EXCELDIR\0"
                   "MaxScanRows=20\0");
```

Tenga en cuenta que el origen de datos es realmente un directorio (C:\EXCELDIR); este directorio debe existir. El controlador de Excel utiliza directorios como orígenes de datos y archivos como tablas individuales (una tabla por archivo. xls).

Para obtener más información acerca de la creación de tablas, vea [origen de datos: crear una tabla en un origen de datos ODBC mediante programación](../../data/odbc/data-source-programmatically-creating-a-table-in-an-odbc-data-source.md).

La siguiente información describe los parámetros que deben pasarse a la función de la API de ODBC `::SQLConfigDataSource`. Para usar `::SQLConfigDataSource`, debe incluir el archivo de encabezado Odbcinst. h y usar la biblioteca de importación Odbcinst. lib. Además, odbccp32. dll debe encontrarse en la ruta de acceso en tiempo de ejecución (o Odbcinst. dll para 16 bits).

Puede crear un nombre de origen de datos ODBC mediante el administrador ODBC o una utilidad similar. Sin embargo, a veces es conveniente crear un nombre de origen de datos directamente desde la aplicación para obtener acceso sin necesidad de que el usuario ejecute una utilidad independiente.

El administrador de ODBC (normalmente instalado en el panel de control) crea un nuevo origen de datos colocando entradas en el registro de Windows (o, para 16 bits, en el archivo ODBC. ini). El administrador de controladores ODBC consulta este archivo para obtener la información necesaria sobre el origen de datos. Es importante saber qué información debe colocarse en el registro porque debe proporcionarla con la llamada a `::SQLConfigDataSource`.

Aunque esta información podría escribirse directamente en el registro sin usar `::SQLConfigDataSource`, cualquier aplicación que lo hace se basa en la técnica actual que usa el administrador de controladores para mantener sus datos. Si una revisión posterior del administrador de controladores ODBC implementa la conservación de registros sobre orígenes de datos de forma diferente, se interrumpirá cualquier aplicación que use esta técnica. Por lo general, es aconsejable utilizar una función de la API cuando se proporciona una. Por ejemplo, el código es portable de 16 bits a 32 bits si se usa la función `::SQLConfigDataSource`, porque la función escribe correctamente en el archivo ODBC. ini o en el registro.

##  <a name="sqlconfigdatasource-parameters"></a><a name="_core_sqlconfigdatasource_parameters"></a>Parámetros de SQLConfigDataSource

A continuación se explican los parámetros de la función `::SQLConfigDataSource`. Gran parte de la información se obtiene de la *Referencia del programador* de la API de C++ ODBC proporcionada con Visual versión 1,5 y versiones posteriores.

###  <a name="function-prototype"></a><a name="_core_function_prototype"></a>Prototipo de función

```
BOOL SQLConfigDataSource(HWND hwndParent,UINT fRequest, LPCSTR lpszDriver, LPCSTR lpszAttributes);
```

### <a name="remarks"></a>Observaciones

####  <a name="parameters-and-usage"></a><a name="_core_parameters_and_usage"></a>Parámetros y uso

*hwndParent*<br/>
La ventana especificada como propietario de los cuadros de diálogo que el administrador de controladores ODBC o el controlador ODBC específico crea para obtener información adicional del usuario sobre el nuevo origen de datos. Si el parámetro *lpszAttributes* no proporciona suficiente información, aparece un cuadro de diálogo. El parámetro *hwndParent* puede ser null.

*lpszDriver*<br/>
La descripción del controlador. Este es el nombre que se presenta a los usuarios en lugar del nombre del controlador físico (el archivo DLL).

*lpszAttributes*<br/>
Lista de atributos con el formato "clave = valor". Estas cadenas se separan mediante terminadores nulos con dos terminadores nulos consecutivos al final de la lista. Estos atributos son principalmente entradas predeterminadas específicas del controlador, que entran en el registro para el nuevo origen de datos. Una clave importante que no se menciona en la referencia de la API de ODBC para esta función es "DSN" ("nombre del origen de datos"), que especifica el nombre del nuevo origen de datos. El resto de las entradas son específicas del controlador para el nuevo origen de datos. A menudo no es necesario proporcionar todas las entradas, ya que el controlador puede preguntar al usuario con los cuadros de diálogo de los nuevos valores. (Establezca *hwndParent* en null para que esto sea así). Es posible que desee proporcionar explícitamente valores predeterminados para que no se le solicite al usuario.

#### <a name="to-determine-the-description-of-a-driver-for-the-lpszdriver-parameter-using-odbc-administrator"></a>Para determinar la descripción de un controlador para el parámetro lpszDriver mediante el administrador de ODBC

1. Ejecute el administrador de ODBC.

1. Haga clic en **Agregar**.

Esto le proporciona una lista de los controladores instalados y sus descripciones. Use esta descripción como el parámetro *lpszDriver* . Tenga en cuenta que usa la descripción completa, como "archivos de Excel (*. xls)", incluida la extensión de nombre de archivo y los paréntesis si existen en la descripción.

Como alternativa, puede examinar el registro (o, para 16 bits, el archivo Odbcinst. ini), que contiene una lista de todas las entradas de controladores y descripciones de la clave del registro "ODBC drivers" (o la sección [ODBC drivers] de Odbcinst. ini).

Una manera de buscar los valores y nombres para el parámetro *lpszAttributes* es examinar el archivo ODBC. ini para un origen de datos ya configurado (quizás uno configurado por el administrador de ODBC).

#### <a name="to-find-keynames-and-values-for-the-lpszattributes-parameter"></a>Para buscar nombres y valores para el parámetro lpszAttributes

1. Ejecute el editor del registro de Windows (o, para 16 bits, abra el archivo ODBC. ini).

1. Busque la información de orígenes de datos ODBC mediante una de las siguientes opciones:

   - Para 32 bits, busque la clave **HKEY_CURRENT_USER \software\odbc\odbc. INI\ODBC orígenes de datos** en el panel izquierdo.

      En el panel derecho se muestran las entradas del formulario: "pub: REG_SZ: *\<nombre del origen de datos >* ", donde *\<nombre del origen de datos >* es un origen de datos que ya se ha configurado con la configuración deseada para el controlador que desea usar. Seleccione el origen de datos que desee, por ejemplo, SQL Server. Los elementos que siguen a la cadena "pub:" son, en orden, el valor de clave y el valor que se usarán en el parámetro *lpszAttributes* .

   - Para 16 bits, busque la sección en el archivo ODBC. ini marcado por [ *\<nombre del origen de datos >* ].

      Las líneas que siguen a esta línea tienen el formato "clave = valor". Se trata exactamente de las entradas que se van a usar en el parámetro *lpszAttributes* .

También puede que desee examinar la documentación del controlador específico que va a usar. Puede encontrar información útil en la ayuda en pantalla del controlador, al que puede tener acceso mediante la ejecución del administrador de ODBC. Normalmente, estos archivos de ayuda se colocan en el directorio WINDOWS\SYSTEM de Windows NT, Windows 3,1 o Windows 95.

#### <a name="to-obtain-online-help-for-your-odbc-driver"></a>Para obtener ayuda en línea para el controlador ODBC

1. Ejecute el administrador de ODBC.

1. Haga clic en **Agregar**.

1. Seleccione el nombre del controlador.

1. Haga clic en **OK**.

Cuando el administrador de ODBC muestre la información para crear un nuevo origen de datos para ese controlador concreto, haga clic en **ayuda**. Esto abre el archivo de ayuda para ese controlador en particular, que normalmente contiene información importante sobre el uso del controlador.

## <a name="see-also"></a>Consulte también

[Origen de datos (ODBC)](../../data/odbc/data-source-odbc.md)
