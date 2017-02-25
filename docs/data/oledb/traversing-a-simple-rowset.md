---
title: "Recorrer un conjunto de filas simple | Microsoft Docs"
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
  - "acceso a datos [C++], conjuntos de filas"
  - "consumidores OLE DB [C++], atributos de bases de datos"
  - "conjuntos de filas [C++], obtener acceso"
  - "conjuntos de filas simples"
ms.assetid: b45acf16-4029-429d-ab8d-b7fba98b9740
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Recorrer un conjunto de filas simple
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El ejemplo siguiente muestra un tipo de acceso a bases de datos fácil y rápido que no incluye el uso de comandos.  El código de consumidor siguiente, perteneciente a un proyecto ATL, recupera los registros de una tabla denominada *Artists* de una tabla de Microsoft Access, usando el proveedor OLE DB de Microsoft para ODBC.  En el código se crea un objeto de tabla [CTable](../../data/oledb/ctable-class.md) con un descriptor de acceso basado en la clase de registro de usuario `CArtists`.  Abre una conexión, abre una sesión en la conexión y abre la tabla en la sesión.  
  
```  
#include <atldbcli.h>  
  
CDataSource connection;  
CSession session;  
CTable<CAccessor<CArtists> > artists;  
  
// Open the connection, session, and table, specifying authentication   
// using Windows NT integrated security. Hard-coding a password is a major  
// security weakness.  
connection.Open(CLSID_MSDASQL, "NWind", NULL, NULL,   
DBPROP_AUTH_INTEGRATED);  
session.Open(connection);  
artists.Open(session, "Artists");  
  
// Get data from the rowset  
while (artists.MoveNext() == S_OK)  
{  
   cout << artists.m_szFirstName;  
   cout << artists.m_szLastName;  
}  
```  
  
 El registro de usuario, `CArtists` , ofrece el siguiente aspecto:  
  
```  
class CArtists  
{  
public:  
// Data Elements  
   CHAR m_szFirstName[20];  
   CHAR m_szLastName[30];  
   short m_nAge;  
  
// Column binding map  
BEGIN_COLUMN_MAP(CArtists)  
   COLUMN_ENTRY(1, m_szFirstName)  
   COLUMN_ENTRY(2, m_szLastName)  
   COLUMN_ENTRY(3, m_nAge)  
END_COLUMN_MAP()  
```  
  
## Vea también  
 [Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)