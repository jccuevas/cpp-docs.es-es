---
title: Utilizar varios descriptores de acceso en un conjunto de filas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BEGIN_ACCESSOR macro
- BEGIN_ACCESSOR macro, multiple accessors
- rowsets [C++], multiple accessors
- accessors [C++], rowsets
ms.assetid: 80d4dc5d-4940-4a28-a4ee-d8602f71d2a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b3d6d41bb705559711187b58243772b668734b16
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336718"
---
# <a name="using-multiple-accessors-on-a-rowset"></a>Utilizar varios descriptores de acceso en un conjunto de filas
Hay tres escenarios básicos en el que se deba usar varios descriptores de acceso:  
  
-   **Varios conjuntos de filas de lectura/escritura.** En este escenario, tiene una tabla con una clave principal. Desea poder leer todas las columnas de la fila, incluida la clave principal. También desea ser capaz de escribir datos en todas las columnas excepto la clave principal (porque no se puede escribir en la columna de clave principal). En este caso, configure dos descriptores de acceso:  
  
    -   Descriptor de acceso 0 contiene todas las columnas.  
  
    -   Descriptor de acceso 1 contiene todas las columnas excepto la clave principal.  
  
-   **Rendimiento.** En este escenario, una o varias columnas contienen una gran cantidad de datos, por ejemplo, gráficos, sonido, archivos o de vídeo. Cada vez que se pasa a una fila, probablemente no desea recuperar la columna con el archivo de datos de gran tamaño, porque si lo hace así una reducción de rendimiento de la aplicación.  
  
     Puede configurar los descriptores de acceso independientes en el que el primer descriptor de acceso contiene todas las columnas excepto la gran cantidad de datos y recupera datos de estas columnas automáticamente; Este es el descriptor de acceso automáticamente. El segundo descriptor de acceso recupera solo la columna que contiene datos de gran tamaño, pero no recupera datos de esta columna automáticamente. Actualizar o recuperar los datos de gran tamaño a petición se pueden utilizar otros métodos.  
  
    -   Descriptor de acceso 0 es automático; Recupera todas las columnas excepto la gran cantidad de datos.  
  
    -   Descriptor de acceso 1 no es un descriptor de acceso automático; Recupera la columna con datos de gran tamaño.  
  
     Utilice el argumento automático para especificar si el descriptor de acceso es automático.  
  
-   **Varias columnas ISequentialStream.** En este escenario, tiene más de una columna que contiene `ISequentialStream` datos. Sin embargo, cada descriptor de acceso está limitado a uno `ISequentialStream` flujo de datos. Para solucionar este problema, configure varios descriptores de acceso, cada uno con uno `ISequentialStream` puntero.  
  
 Normalmente crean los descriptores de acceso mediante la [BEGIN_ACCESSOR](../../data/oledb/begin-accessor.md) y [END_ACCESSOR](../../data/oledb/end-accessor.md) macros. También puede usar el [db_accessor](../../windows/db-accessor.md) atributo. (Se describe con más detalle en los descriptores de acceso [registros de usuario](../../data/oledb/user-records.md).) Las macros o el atributo especifican si un descriptor de acceso es automático o un descriptor de acceso no automático:  
  
-   En un descriptor de acceso automático, los métodos de desplazamiento como `MoveFirst`, `MoveLast`, `MoveNext`, y `MovePrev` recuperar datos para todas las columnas especificadas automáticamente. Descriptor de acceso 0 debe ser el descriptor de acceso automático.  
  
-   En un descriptor de acceso no automático, la recuperación no se produce hasta que se llame explícitamente a un método como `Update`, `Insert`, `Fetch`, o `Delete`. En los escenarios descritos anteriormente, es posible que no desea recuperar todas las columnas en cada movimiento. Puede colocar una o varias columnas en un descriptor de acceso independiente y hacer un descriptor de acceso no automáticas, como se muestra a continuación.  
  
 El ejemplo siguiente utiliza varios descriptores de acceso para leer y escribir en la tabla de trabajos de la base de datos pubs de SQL Server. Este es el uso más común de varios descriptores de acceso; consulte el escenario de "varios conjuntos de filas de lectura/escritura" anterior.  
  
 La clase de registro de usuario es como sigue. Configura dos descriptores de acceso: el descriptor de acceso 0 contiene solo la columna de clave principal (ID) y descriptor de acceso 1 contiene otras columnas.  
  
```cpp  
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
  
 El código principal es como sigue. Una llamada a `MoveNext` recupera automáticamente los datos del identificador de la columna de clave principal mediante el descriptor de acceso 0. Tenga en cuenta cómo el `Insert` método cerca del descriptor de acceso final usa 1 para evitar escribir en la columna de clave principal.  
  
```cpp  
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
            CTable<CAccessor<CJobs>> jobs;  
  
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
  
## <a name="see-also"></a>Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)   
 [Registros de usuario](../../data/oledb/user-records.md)