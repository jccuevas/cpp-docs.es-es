---
title: "Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente | Microsoft Docs"
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
  - "estado de campos en plantillas OLE DB"
  - "plantillas de consumidor OLE DB, estado de campos"
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Al usar el Asistente para consumidores OLE DB ATL con el fin de crear un consumidor, el asistente genera un miembro de datos en la clase de registro de usuario por cada campo que especifique en el mapa de columnas.  Cada miembro de datos es del tipo `DWORD` y contiene un valor de estado correspondiente a su campo respectivo.  
  
 Por ejemplo, para un miembro de datos *m\_OwnerID*, el asistente genera un miembro de datos adicional para el estado del campo \(*dwOwnerIDStatus*\), y otro para la longitud del campo \(*dwOwnerIDLength*\).  También genera un mapa de columnas con entradas `COLUMN_ENTRY_LENGTH_STATUS`.  
  
 Esto queda reflejado en el ejemplo de código siguiente:  
  
```  
[db_source("insert connection string")]  
[db_command(" \  
   SELECT \  
      Au_ID, \  
      Author, \  
      `Year Born`, \  
      FROM Authors")]  
  
class CAuthors  
{  
public:  
  
   // The following wizard-generated data members contain status   
   // values for the corresponding fields in the column map. You   
   // can use these values to hold NULL values that the database   
   // returns or to hold error information when the compiler returns   
   // errors. See "Field Status Data Members in Wizard-Generated   
   // Accessors" in the Visual C++ documentation for more information   
   // on using these fields.  
   DWORD m_dwAuIDStatus;  
   DWORD m_dwAuthorStatus;  
   DWORD m_dwYearBornStatus;  
  
   // The following wizard-generated data members contain length  
   // values for the corresponding fields in the column map.  
   DWORD m_dwAuIDLength;  
   DWORD m_dwAuthorLength;  
   DWORD m_dwYearBornLength;  
  
BEGIN_COLUMN_MAP(CAuthorsAccessor)  
   COLUMN_ENTRY_LENGTH_STATUS(1, m_AuID, dwAuIDLength, dwAuIDStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(2, m_Author, dwAuthorLength, dwAuthorStatus)  
   COLUMN_ENTRY_LENGTH_STATUS(3, m_YearBorn, dwYearBornLength, dwYearBornStatus)  
END_COLUMN_MAP()  
  
   [ db_column(1, status=m_dwAuIDStatus, length=m_dwAuIDLength) ] LONG m_AuID;  
   [ db_column(2, status=m_dwAuthorStatus, length=m_dwAuthorLength) ] TCHAR m_Author[51];  
   [ db_column(3, status=m_dwYearBornStatus, length=m_dwYearBornLength) ] SHORT m_YearBorn;  
  
   void GetRowsetProperties(CDBPropSet* pPropSet)  
   {  
      pPropSet->AddProperty(DBPROP_IRowsetChange, true);  
      pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);  
   }  
};  
```  
  
> [!NOTE]
>  Si se modifica la clase de registro de usuario o se crea un consumidor personalizado, las variables de datos deben figurar antes que las de estado y longitud.  
  
 Se pueden usar los valores de estado con fines de depuración.  Si el código generado por el Asistente para consumidores OLE DB ATL genera errores de compilación como **DB\_S\_ERRORSOCCURRED** o **DB\_E\_ERRORSOCCURRED**, se deben examinar en primer lugar los valores actuales de los miembros de datos del estado de campo.  Aquellos que tengan valores distintos de cero corresponderán a las columnas que dieron lugar al error.  
  
 También se pueden usar los valores de estado para establecer un valor NULL para un campo particular.  Hacerlo resulta útil en casos en los que se desee distinguir un valor de campo como NULL en lugar de cero.  Corresponde al programador decidir si NULL es un valor válido o un valor especial, así como la forma en que debe tratarlo la aplicación.  OLE DB define **DBSTATUS\_S\_ISNULL** como la forma correcta de especificar un valor NULL genérico.  Si el consumidor lee datos y el valor es null, el campo de estado se establece en **DBSTATUS\_S\_ISNULL**.  Si el consumidor desea establecer un valor NULL, el consumidor establece el valor de estado en **DBSTATUS\_S\_ISNULL** antes de llamar al proveedor.  
  
 A continuación, abra Oledb.h y busque **DBSTATUSENUM**.  Puede comparar el valor numérico del estado distinto de cero con los valores de la enumeración **DBSTATUSENUM**.  Si el nombre de la enumeración no basta para saber cuál es incorrecto, vea el tema “status” en la sección “binding data values” de. [La guía del programador de OLE DB](http://go.microsoft.com/fwlink/?LinkId=121548) Este tema contiene tablas de valores de estado que se usan a la hora de obtener o establecer datos.  Para obtener información sobre los valores de longitud, vea el tema "Length" en la misma sección.  
  
## Recuperar la longitud o el estado de una columna  
 Se puede recuperar la longitud de una columna de longitud variable o el estado de una columna \(para buscar **DBSTATUS\_S\_ISNULL**, por ejemplo\):  
  
-   Para obtener la longitud, use la macro `COLUMN_ENTRY_LENGTH`.  
  
-   Para obtener el estado, use la macro `COLUMN_ENTRY_STATUS`.  
  
-   Para obtener ambos, use `COLUMN_ENTRY_LENGTH_STATUS`, como se muestra a continuación.  
  
```  
class CProducts  
{  
public:  
   char      szName[40];  
   long      nNameLength;  
   DBSTATUS   nNameStatus;  
  
BEGIN_COLUMN_MAP(CProducts)  
// Bind the column to CProducts.m_ProductName.  
// nOrdinal is zero-based, so the column number of m_ProductName is 1.  
   COLUMN_ENTRY_LENGTH_STATUS(1, szName, nNameLength, nNameStatus)  
END_COLUMN_MAP()  
};  
  
CTable<CAccessor<CProducts > > product;  
  
product.Open(session, "Product");  
while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
 Al utilizar `CDynamicAccessor`, la longitud y el estado se enlazan automáticamente.  Para recuperar los valores de longitud y estado, use las funciones miembro `GetLength` y **GetStatus**.  
  
## Vea también  
 [Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)