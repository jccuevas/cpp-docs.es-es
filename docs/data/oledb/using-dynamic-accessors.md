---
title: "Utilizar descriptores de acceso din&#225;micos | Microsoft Docs"
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
  - "descriptores de acceso [C++], dinámico"
  - "descriptores de acceso dinámicos"
ms.assetid: e5d5bfa6-2b1d-49d0-8ced-914666422431
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Utilizar descriptores de acceso din&#225;micos
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Los descriptores de acceso dinámicos permiten el acceso a un origen de datos cuando no se conoce el esquema \(estructura subyacente\) de la base de datos.  La biblioteca de plantillas OLE DB proporciona varias clases para ayudarle.  
  
 En el ejemplo [DynamicConsumer](http://msdn.microsoft.com/es-es/2ccc4c61-6749-4e83-aa81-00f8009c0dc3) se muestra cómo usar las clases de descriptor de acceso dinámico para obtener información de columnas y crear dinámicamente descriptores de acceso.  
  
## Utilizar CDynamicAccessor  
 [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) permite tener acceso a un origen de datos cuando no conoce el esquema de base de datos \(la estructura subyacente de la base de datos\).  Los métodos `CDynamicAccessor` obtienen información de columna como su nombre, recuento y tipo de datos.  Utilice esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  La información de columnas se almacena en un búfer creado y administrado por esta clase.  Para obtener datos del búfer, utilice el método [GetValue](../../data/oledb/cdynamicaccessor-getvalue.md).  
  
## Ejemplo  
  
### Código  
  
```  
// Using_Dynamic_Accessors.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
  
    CDataSource ds;  
    CSession ss;  
  
    CTable<CDynamicAccessor> rs;  
  
    // The following is an example initialization string:  
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"  
      L"Integrated Security=SSPI;Persist Security Info=False;"  
      L"Initial Catalog=Loginname;Data Source=your_data_source;"  
      L"Use Procedure for Prepare=1;Auto Translate=True;"  
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"  
      L"Use Encryption for Data=False;"  
      L"Tag with column collation when possible=False");  
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            DBTYPE type;  
            rs.GetColumnType( i, &type );  
            printf_s( "Column %d [%S] is of type %d\n",  
                      i, rs.GetColumnName( i ), type );   
  
            switch( type )  
            {  
                case DBTYPE_WSTR:  
                    printf_s( "value is %S\n",  
                              (WCHAR*)rs.GetValue( i ) );  
                break;  
                case DBTYPE_STR:  
                    printf_s( "value is %s\n",  
                              (CHAR*)rs.GetValue( i ) );  
                default:  
                    printf_s( "value is %d\n",  
                              *(long*)rs.GetValue( i ) );  
            }  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
    return 0;  
}  
```  
  
## Utilizar CDynamicStringAccessor  
 [CDynamicStringAccessor](../../data/oledb/cdynamicstringaccessor-class.md) funciona igual que [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), salvo en un aspecto importante.  Si bien `CDynamicAccessor` solicita datos en el formato nativo compatible con el proveedor, `CDynamicStringAccessor` solicita que el proveedor recupere todos los datos a los que se tuvo acceso desde el almacén de datos como datos de cadena.  Esto es de especial utilidad para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como mostrar o imprimir su contenido.  
  
 Para obtener información de columnas, utilice métodos `CDynamicStringAccessor`.  Utilice esta información de columna para crear un descriptor de acceso dinámicamente en tiempo de ejecución.  La información de columnas se almacena en un búfer creado y administrado por esta clase.  Para obtener datos del búfer, utilice [CDynamicStringAccessor::GetString](../../data/oledb/cdynamicstringaccessor-getstring.md); para almacenar datos en el búfer, utilice [CDynamicStringAccessor::SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).  
  
## Ejemplo  
  
### Código  
  
```  
// Using_Dynamic_Accessors_b.cpp  
// compile with: /c /EHsc  
#include <stdio.h>  
#include <objbase.h>  
#include <atldbcli.h>  
  
int main( int argc, char* argv[] )  
{  
    HRESULT hr = CoInitialize( NULL );  
    if (hr != S_OK)  
    {  
        exit (-1);  
    }  
  
    CDataSource ds;  
    CSession ss;  
  
    CTable<CDynamicStringAccessor> rs;  
  
    // The following is an example initialization string:  
    hr = ds.OpenFromInitializationString(L"Provider=SQLOLEDB.1;"  
      L"Integrated Security=SSPI;Persist Security Info=False;"  
      L"Initial Catalog=Loginname;Data Source=your_data_source;"  
      L"Use Procedure for Prepare=1;Auto Translate=True;"  
      L"Packet Size=4096;Workstation ID=LOGINNAME01;"  
      L"Use Encryption for Data=False;"  
      L"Tag with column collation when possible=False");  
  
    hr = ss.Open( ds );  
    hr = rs.Open( ss, "Shippers" );  
  
    hr = rs.MoveFirst( );  
    while( SUCCEEDED( hr ) && hr != DB_S_ENDOFROWSET )  
    {  
        for( size_t i = 1; i <= rs.GetColumnCount( ); i++ )  
        {  
            printf_s( "column %d value is %s\n",   
                      i, rs.GetString( i ) );  
        }  
        hr = rs.MoveNext( );  
    }  
  
    rs.Close();     
    ss.Close();  
    ds.Close();  
    CoUninitialize();  
  
   return 0;  
  
}  
```  
  
## Utilizar CDynamicParameterAccessor  
 [CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-class.md) es similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md), excepto que `CDynamicParameterAccessor` obtiene la información de parámetros que se debe establecer mediante una llamada a la interfaz [ICommandWithParameters](https://msdn.microsoft.com/en-us/library/ms712937.aspx).  El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.  
  
 La información de parámetros se almacena en un búfer creado y administrado por esta clase.  Para obtener los datos de parámetros del búfer, utilice [CDynamicParameterAccessor::GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [CDynamicParameterAccessor::GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).  
  
 Para consultar un ejemplo que muestra cómo utilizar esta clase para ejecutar un procedimiento almacenado de SQL Server y obtener los valores de parámetros de salida, vea el artículo de Knowledge Base Q058860, "HOWTO: Execute Stored Procedure using CDynamicParameterAccessor". Los artículos de Knowledge Base están disponibles en la documentación de Visual Studio de MSDN Library o en [http:\/\/support.microsoft.com](http://support.microsoft.com/).  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [CDynamicAccessor \(Clase\)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor \(Clase\)](../../data/oledb/cdynamicstringaccessor-class.md)   
 [CDynamicParameterAccessor \(Clase\)](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [DynamicConsumer Sample](http://msdn.microsoft.com/es-es/2ccc4c61-6749-4e83-aa81-00f8009c0dc3)