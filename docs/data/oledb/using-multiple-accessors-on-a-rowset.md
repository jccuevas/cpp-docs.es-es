---
title: "Utilizar varios descriptores de acceso en un conjunto de filas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "descriptores de acceso [C++], conjuntos de filas"
  - "BEGIN_ACCESSOR (macro)"
  - "BEGIN_ACCESSOR (macro), múltiples descriptores de acceso"
  - "conjuntos de filas [C++], múltiples descriptores de acceso"
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Utilizar varios descriptores de acceso en un conjunto de filas
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hay tres escenarios básicos en los que es necesario utilizar varios descriptores de acceso:  
  
-   **Varios conjuntos de filas de lectura y escritura.** En este caso, existe una tabla con una clave principal.  Se desea poder leer todas las columnas de la fila, incluida la clave principal.  Se desea también poder escribir datos en todas las columnas, excepto la clave principal \(dado que no es posible escribir en la columna de clave principal\).  En este caso, se configuran dos descriptores de acceso:  
  
    -   El descriptor de acceso 0 contiene todas las columnas.  
  
    -   El descriptor de acceso 1 contiene todas las columnas excepto la clave principal.  
  
-   **Rendimiento.** En este caso, una o varias columnas contienen una gran cantidad de datos, por ejemplo, archivos gráficos, de sonido o de vídeo.  Cada vez que se desplaza a una fila, es probable que no desee recuperar la columna que contiene el archivo de datos grande, porque eso haría disminuir el rendimiento de la aplicación.  
  
     Se pueden configurar descriptores de acceso independientes, de los cuales el primero contenga todas las columnas excepto la que contiene gran cantidad de datos y recupere los datos de las columnas automáticamente; éste es el descriptor de acceso automático.  El segundo descriptor de acceso sólo recupera la columna que contiene gran cantidad de datos, pero no lo hace de forma automática.  Se pueden utilizar otros métodos para actualizar o recuperar los datos de gran tamaño a petición.  
  
    -   El descriptor de acceso 0 es un descriptor de acceso automático; recupera todas las columnas excepto la que contiene gran cantidad de datos.  
  
    -   El descriptor de acceso 1 no es un descriptor de acceso automático; recupera la columna que contiene gran cantidad de datos.  
  
     Utilice el argumento automático para especificar si el descriptor de acceso es automático.  
  
-   **Varias columnas ISequentialStream.** En este escenario, existen varias columnas que contienen datos `ISequentialStream`.  Sin embargo, cada descriptor de acceso está limitado a un flujo de datos `ISequentialStream`.  Para solucionar este problema, configure varios descriptores de acceso, cada uno con un puntero `ISequentialStream`.  
  
 Normalmente, los descriptores de acceso se crean mediante las macros [BEGIN\_ACCESSOR](../../data/oledb/begin-accessor.md) y [END\_ACCESSOR](../../data/oledb/end-accessor.md).  También se puede utilizar el atributo [db\_accessor](../../windows/db-accessor.md). Los descriptores de acceso se describen con más detalle en [Registros de usuario](../../data/oledb/user-records.md). Las macros o el atributo especifican si un descriptor de acceso es automático o no:  
  
-   En un descriptor de acceso automático, los métodos de desplazamiento como **MoveFirst**, `MoveLast`, `MoveNext` y `MovePrev` recuperan automáticamente datos de todas las columnas especificadas.  El descriptor de acceso 0 debe ser el descriptor de acceso automático.  
  
-   En un descriptor de acceso no automático, la recuperación no se produce hasta que se llama de forma explícita a un método como **Update**, **Insert**, **Fetch** o **Delete**.  En los escenarios descritos anteriormente, puede que no se desee recuperar todas las columnas en cada desplazamiento.  Se pueden colocar una o varias columnas en un descriptor de acceso independiente y convertirlo en descriptor de acceso automático, como se muestra a continuación.  
  
 En el ejemplo siguiente se utilizan varios descriptores de acceso para leer y escribir en la tabla Jobs de la base de datos Pubs de SQL Server.  Este uso de los descriptores de acceso es el más común; vea el escenario acerca de "varios conjuntos de filas de lectura y escritura" más atrás.  
  
 La clase de registro de usuario es como sigue.  Se configuran dos descriptores de acceso: el descriptor de acceso 0 sólo contiene la columna de clave principal \(ID\) y el descriptor de acceso 1 contiene las demás columnas.  
  
```  
class CJobs  
{  
public:  
    enum {  
        sizeOfDescription = 51  
    };  
  
    short nID;  
    char szDescription[ sizeOfDescription ];  
    short nMinLvl;  
    short nMaxLvl;  
  
    DWORD dwID;  
    DWORD dwDescription;  
    DWORD dwMinLvl;  
    DWORD dwMaxLvl;  
  
BEGIN_ACCESSOR_MAP(CJobs, 2)  
    // Accessor 0 is the automatic accessor  
    BEGIN_ACCESSOR(0, true)  
        COLUMN_ENTRY_STATUS(1, nID, dwID)  
    END_ACCESSOR()  
    // Accessor 1 is the non-automatic accessor  
    BEGIN_ACCESSOR(1, true)  
        COLUMN_ENTRY_STATUS(2, szDescription, dwDescription)  
        COLUMN_ENTRY_STATUS(3, nMinLvl, dwMinLvl)  
        COLUMN_ENTRY_STATUS(4, nMaxLvl, dwMaxLvl)  
    END_ACCESSOR()  
END_ACCESSOR_MAP()  
};  
```  
  
 El código principal es el siguiente.  Con la llamada a `MoveNext`, se recuperan automáticamente los datos del identificador de columna de la clave principal mediante el descriptor de acceso 0.  Observe como el método **Insert** del final usa el descriptor de acceso 1 para evitar escribir en la columna de la clave principal.  
  
```  
int main(int argc, char* argv[])  
{  
    // Initalize COM  
    ::CoInitialize(NULL);  
  
    // Create instances of the data source and session  
    CDataSource source;  
    CSession session;  
    HRESULT hr = S_OK;  
  
    // Set initialization properties  
    CDBPropSet dbinit(DBPROPSET_DBINIT);  
    dbinit.AddProperty(DBPROP_AUTH_USERID, OLESTR("my_user_id"));  
    dbinit.AddProperty(DBPROP_INIT_CATALOG, OLESTR("pubs"));  
    dbinit.AddProperty(DBPROP_INIT_DATASOURCE, OLESTR("(local)"));  
  
    hr = source.Open("SQLOLEDB.1", &dbinit);  
    if (hr == S_OK)  
    {  
        hr = session.Open(source);  
        if (hr == S_OK)  
        {  
            // Ready to fetch/access data  
            CTable<CAccessor<CJobs> > jobs;  
  
            // Set properties for making the rowset a read/write cursor  
            CDBPropSet dbRowset(DBPROPSET_ROWSET);  
            dbRowset.AddProperty(DBPROP_CANFETCHBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_CANSCROLLBACKWARDS, true);  
            dbRowset.AddProperty(DBPROP_IRowsetChange, true);  
            dbRowset.AddProperty(DBPROP_UPDATABILITY,  
                DBPROPVAL_UP_INSERT | DBPROPVAL_UP_CHANGE |  
                DBPROPVAL_UP_DELETE);  
  
            hr = jobs.Open(session, "jobs", &dbRowset);  
            if (hr == S_OK)  
            {  
                // Calling MoveNext automatically retrieves ID  
                // (using accessor 0)  
                while(jobs.MoveNext() == S_OK)  
                   printf_s("Description = %s\n", jobs.szDescription);  
  
                hr = jobs.MoveFirst();  
                if (hr == S_OK)  
                {  
                    jobs.nID = 25;  
                    strcpy_s(&jobs.szDescription[0],  
                             jobs.sizeOfDescription,  
                             "Developer");  
                    jobs.nMinLvl = 10;  
                    jobs.nMaxLvl = 20;  
  
                    jobs.dwDescription = DBSTATUS_S_OK;  
                    jobs.dwID = DBSTATUS_S_OK;  
                    jobs.dwMaxLvl = DBSTATUS_S_OK;  
                    jobs.dwMinLvl = DBSTATUS_S_OK;  
  
                    // Insert method uses accessor 1  
                    // (to avoid writing to the primary key column)  
                    hr = jobs.Insert(1);     
                }  
                jobs.Close();  
            }  
            session.Close();  
        }  
        source.Close();  
    }  
  
    // Uninitialize COM  
    ::CoUninitialize();  
    return 0;  
}  
```  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [Registros de usuario](../../data/oledb/user-records.md)