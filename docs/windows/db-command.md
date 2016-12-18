---
title: "db_command | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "vc-attr.db_command"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "db_command (atributo)"
ms.assetid: 714c3e15-85d7-408b-9a7c-88505c3e5d24
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# db_command
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crea un comando OLE DB.  
  
## Sintaxis  
  
```  
  
[ db_command(   
command  
,   
   name  
,   
   source_name  
,   
   hresult  
,   
   bindings  
,   
   bulk_fetch  
)  
]  
  
```  
  
#### Parámetros  
 `command`  
 Cadena de comandos que contiene el texto de un comando OLE DB. Veamos un ejemplo sencillo:  
  
```  
[ db_command ( command = "Select * from Products" ) ]  
```  
  
 La sintaxis del *comando* es la siguiente:  
  
```  
binding parameter block 1  
   OLE DB command  
binding parameter block 2  
   continuation of OLE DB command  
binding parameter block 3  
...  
```  
  
 Se define *un bloque de parámetros de enlace* del siguiente modo:  
  
 **\(\[** `bindtype` **\]** *szVar1* \[*, szVar2* \[, *nVar3* \[, ...\]\]\] **\)**  
  
 donde:  
  
 **\(** marca el inicio del bloque de enlace de datos.  
  
 **\[** `bindtype` **\]** es una de las siguientes cadenas que no distinguen mayúsculas de minúsculas:  
  
-   **\[db\_column\]** enlaza todas las variables de miembro con una columna en un conjunto de filas.  
  
-   **\[bindto\]** \(igual que **\[db\_column\]**\).  
  
-   **\[in\]** enlaza variables de miembro como parámetros de entrada.  
  
-   **\[out\]** enlaza variables de miembro como parámetros de salida.  
  
-   **\[in,out\]** enlaza variables de miembro como parámetros de entrada\/salida.  
  
 *SzVarX* se resuelve como una variable de miembro dentro del ámbito actual.  
  
 **\)** marca el final del bloque de enlace de datos.  
  
 Si la cadena de comandos contiene uno o varios especificadores como \[in\], \[out\] o \[in\/out\], **db\_command** compila una asignación de parámetro.  
  
 Si la cadena de comandos contiene uno o varios parámetros como \[db\_column\] o \[bindto\], **db\_command** genera un conjunto de filas y una asignación de descriptor de acceso para dar servicio a estas variables enlazadas. Consulte [db\_accessor](../windows/db-accessor.md) para obtener más información.  
  
> [!NOTE]
>  La sintaxis \[`bindtype`\] y el parámetro `bindings` no son válidos cuando se usa **db\_command** en el nivel de clase.  
  
 A continuación se muestran algunos ejemplos de bloques de parámetros de enlace. En el siguiente ejemplo se enlazan los miembros de datos `m_au_fname` y `m_au_lname` con las columnas `au_fname` y `au_lname`, respectivamente, de la tabla authors de la base de datos pubs:  
  
```  
TCHAR m_au_fname[21];  
TCHAR m_au_lname[41];  
TCHAR m_state[3] = 'CA';  
  
[db_command (  
   command = "SELECT au_fname([bindto]m_au_fname), au_lname([bindto]m_au_lname) " \  
   "FROM dbo.authors " \  
   "WHERE state = ?([in]m_state)")  
```  
  
 \]  
  
 *name* \(opcional\)  
 Nombre del identificador usado para trabajar con el conjunto de filas. Si especifica *name*, **db\_command** genera una clase con el *name* \(nombre\) especificado, que se puede usar para recorrer el conjunto de filas o para ejecutar varias consultas de acción. Si no especifica *name*, no se podrá devolver al usuario más de una fila de resultados.  
  
 *source\_name* \(opcional\)  
 Variable o instancia `CSession` de una clase que tiene aplicado el atributo `db_source`, en el que se ejecuta el comando. Consulte [db\_source](../windows/db-source.md).  
  
 **db\_command** se asegura de que la variable usada para *source\_name* sea válida, por lo que la variable especificada debe estar en el ámbito global o de función.  
  
 `hresult` \(opcional\)  
 Identifica la variable que recibirá el `HRESULT` de este comando de base de datos. Si la variable no existe, el atributo la insertará automáticamente.  
  
 *bindings* \(opcional\)  
 Le permite separar los parámetros de enlace del comando OLE DB.  
  
 Si especifica un valor para `bindings`, **db\_command** analizará el valor asociado y no analizará el parámetro \[`bindtype`\]. De este modo, puede usar la sintaxis del proveedor OLE DB. Para deshabilitar el análisis sin enlazar parámetros, especifique **Bindings\=""**.  
  
 Si no especifica ningún valor para `bindings`, **db\_command** analizará el bloque de parámetros de enlace en busca de '**\(**', seguido de **\[**`bindtype`**\]** entre corchetes, seguido de una o más variables de miembro de C\+\+ declaradas previamente, seguido de '**\)**'. Todo el texto incluido entre los paréntesis se quitará del comando resultante y los parámetros se usarán para construir los enlaces de columnas y de parámetros para este comando.  
  
 *bulk\_fetch* \(opcional\)  
 Valor entero que especifica el número de filas que se obtendrá.  
  
 El valor predeterminado es 1, que especifica que se obtendrá una única fila \(el conjunto de filas será del tipo [CRowset](../data/oledb/crowset-class.md)\).  
  
 Un valor superior a 1 especifica una obtención de filas masiva. La obtención masiva de filas hace referencia a la capacidad de los conjuntos de filas masivos de obtener varios identificadores de fila \(el conjunto de filas será del tipo [CBulkRowset](../data/oledb/cbulkrowset-class.md) y llamará a `SetRows` con el número de filas especificado\).  
  
 Si *bulk\_fetch* es inferior a uno, `SetRows` devolverá cero.  
  
## Comentarios  
 **db\_command** crea un objeto [CCommand](../data/oledb/ccommand-class.md), usado por un consumidor OLE DB para ejecutar un comando.  
  
 Puede usar **db\_command** con cualquier ámbito de función o clase; la principal diferencia radica en el ámbito del objeto `CCommand`. Con el ámbito de función, los datos tales como los enlaces concluyen al final de la función. El uso de los ámbitos de clase y de función involucra a la clase de plantilla de consumidor OLE DB **CCommand\<\>**, aunque los argumentos de la plantilla difieren en los casos de la función y la clase. En el caso de la función, los enlaces se efectuarán con un **descriptor de acceso** formado por variables locales, mientras que el uso de la clase deducirá una clase derivada de `CAccessor` como argumento. Cuando se usa como atributo de clase, **db\_command** funciona de forma conjunta con **db\_column**.  
  
 Se puede usar **db\_command** para ejecutar comandos que no devuelvan un conjunto de resultados.  
  
 Cuando el proveedor de atributos de consumidor aplica este atributo a una clase, el compilador cambiará el nombre de la clase a \_*NombreClase*DescriptorAcceso, donde *NombreClase* es el nombre asignado a la clase; el compilador también creará una clase denominada *NombreClase*, que deriva de \_*NombreClase*DescriptorAcceso.  En Vista de clases verá ambas clases.  
  
## Ejemplo  
 En este ejemplo se define un comando que selecciona los nombres y apellidos de una tabla en la que la columna state coincide con “CA”.**db\_command** crea y lee un conjunto de filas en el que puede llamar a funciones generadas por el asistente, como [OpenAll y CloseAll](../data/oledb/consumer-wizard-generated-methods.md), así como funciones de miembro `CRowset`, como [MoveNext](../data/oledb/crowset-movenext.md).  
  
 Tenga en cuenta que, en este código, debe proporcionar su propia cadena de conexión que se conecte a la base de datos pubs. Para obtener información sobre cómo hacer esto en el entorno de desarrollo, consulte [How to: Connect to a Database from Server Explorer](http://msdn.microsoft.com/es-es/7c1c3067-0d77-471b-872b-639f9f50db74) y [How to: Add New Data Connections in Server Explorer\/Database Explorer](http://msdn.microsoft.com/es-es/fb2f513b-ddad-4142-911e-856bba0054c8).  
  
```  
// db_command.h  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
  
#pragma once  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
  
struct CAuthors {  
   // In order to fix several issues with some providers, the code below may bind  
   // columns in a different order than reported by the provider  
  
   DBSTATUS m_dwau_lnameStatus;  
   DBSTATUS m_dwau_fnameStatus;  
   DBLENGTH m_dwau_lnameLength;  
   DBLENGTH m_dwau_fnameLength;  
  
   [ db_column("au_lname", status="m_dwau_lnameStatus", length="m_dwau_lnameLength") ] TCHAR m_au_lname[41];  
   [ db_column("au_fname", status="m_dwau_fnameStatus", length="m_dwau_fnameLength") ] TCHAR m_au_fname[21];  
  
   [ db_param("7", paramtype="DBPARAMIO_INPUT") ] TCHAR m_state[3];  
  
   void GetRowsetProperties(CDBPropSet* pPropSet) {  
      pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
      pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);  
   }  
};  
```  
  
## Ejemplo  
  
```  
// db_command.cpp  
// compile with: /c  
#include "db_command.h"  
  
int main(int argc, _TCHAR* argv[]) {  
   HRESULT hr = CoInitialize(NULL);  
  
   // Instantiate rowset  
   CAuthors rs;  
  
   // Open rowset and move to first row  
   strcpy_s(rs.m_state, sizeof(rs.m_state), _T("CA"));  
   hr = rs.OpenAll();  
   hr = rs.MoveFirst();  
  
   // Iterate through the rowset  
   while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET ) {  
      // Print out the column information for each row  
      printf("First Name: %s, Last Name: %s\n", rs.m_au_fname, rs.m_au_lname);  
      hr = rs.MoveNext();  
   }  
  
   rs.CloseAll();  
   CoUninitialize();  
}  
```  
  
## Ejemplo  
 En este ejemplo se usa `db_source` en la clase de origen de datos `CMySource` y `db_command` en las clases de comandos `CCommand1` y `CCommand2`.  
  
```  
// db_command_2.cpp  
// compile with: /c  
#include <atlbase.h>  
#include <atlplus.h>  
#include <atldbcli.h>  
// class usage for both db_source and db_command  
  
[  db_source(L"your connection string"),  
   db_command(L" \  
      SELECT au_lname, au_fname \  
      FROM dbo.authors \  
      WHERE state = 'CA'")  ]  
struct CMySource {  
   HRESULT OpenDataSource() {  
      return S_OK;  
   }  
};  
  
[db_command(command = "SELECT * FROM Products")]  
class CCommand1 {};  
  
[db_command(command = "SELECT FNAME, LNAME FROM Customers")]  
class CCommand2 {};  
  
int main() {  
   CMySource s;  
   HRESULT hr = s.OpenDataSource();  
   if (SUCCEEDED(hr)) {  
      CCommand1 c1;  
      hr = c1.Open(s);  
  
      CCommand2 c2;  
      hr = c2.Open(s);  
   }  
  
   s.CloseDataSource();  
}  
```  
  
## Requisitos  
  
### Contexto de atributo  
  
|||  
|-|-|  
|**Se aplica a**|**clase**, `struct`, miembro, método, local|  
|**Reiterativo**|No|  
|**Atributos requeridos**|Ninguna|  
|**Atributos no válidos**|Ninguna|  
  
 Para obtener más información acerca de los contextos de atributo, consulte [Contextos de atributo](../windows/attribute-contexts.md).  
  
## Vea también  
 [OLE DB Consumer Attributes](../windows/ole-db-consumer-attributes.md)   
 [Stand\-Alone Attributes](../Topic/Stand-Alone%20Attributes.md)   
 [Attributes Samples](http://msdn.microsoft.com/es-es/558ebdb2-082f-44dc-b442-d8d33bf7bdb8)