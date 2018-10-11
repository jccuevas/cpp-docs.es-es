---
title: Campo de estado de los miembros de datos en los descriptores de acceso generados por el Asistente | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB consumer templates, field status
- field status in OLE DB templates
ms.assetid: 66e4e223-c60c-471e-860d-d23abcdfe371
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b1c48f4699c0add937c2bcdb13d49bce8cb895c4
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/11/2018
ms.locfileid: "49083971"
---
# <a name="field-status-data-members-in-wizard-generated-accessors"></a>Miembros de datos sobre el estado de un campo en los descriptores de acceso generados por el asistente

Cuando usa el Asistente para consumidores OLE DB ATL para crear un consumidor, el asistente genera a un miembro de datos en la clase de registro de usuario para cada campo que especifique en el mapa de columnas. Cada miembro de datos es de tipo `DWORD` y contiene un valor de estado correspondiente a su campo correspondiente.  
  
Por ejemplo, para un miembro de datos *m_OwnerID*, el asistente genera un miembro de datos adicionales para el estado de campo (*dwOwnerIDStatus*) y otro para la longitud de campo (*dwOwnerIDLength*). También genera un mapa de columnas con entradas COLUMN_ENTRY_LENGTH_STATUS.  
  
Esto se muestra en el código siguiente:  
  
```cpp  
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
>  Si modifica la clase de registro de usuario o escribe su propio consumidor, las variables de datos deben preceder a las variables de estado y longitud.  
  
Puede usar los valores de estado con fines de depuración. Si el código generado por el Asistente para consumidores OLE DB ATL genera errores de compilación como DB_S_ERRORSOCCURRED o DB_E_ERRORSOCCURRED, debe mirar los valores actuales de los miembros de datos de estado de campo. Aquellos usuarios que tienen valores distintos de cero corresponden a las columnas incorrectos.  
  
También puede usar los valores de estado para establecer un valor NULL para un campo determinado. Esto ayuda a en los casos en los que desee distinguir un valor de campo como NULL en lugar de cero. Depende de usted decidir si NULL es un valor válido o un valor especial y decidir cómo debe controlar su aplicación. OLE DB define DBSTATUS_S_ISNULL como la forma correcta de especificar un valor NULL genérico. Si el consumidor lee los datos y el valor es null, el campo de estado se establece en DBSTATUS_S_ISNULL. Si el consumidor desea establecer un valor NULL, el consumidor establece el valor de estado en DBSTATUS_S_ISNULL antes de llamar al proveedor.  
  
A continuación, abra Oledb.h y busque `DBSTATUSENUM`. A continuación, puede hacer coincidir el valor numérico del estado distinto de cero con el `DBSTATUSENUM` valores de enumeración. Si el nombre de la enumeración no es suficiente para saber cuál es el problema, consulte el tema "Status" en la sección "Valores de datos de enlace" de la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643). Este tema contiene las tablas de valores de estado que se utiliza al obtener o establecer los datos. Para obtener información acerca de los valores de longitud, vea el tema "Length" en la misma sección.  
  
## <a name="retrieving-the-length-or-status-of-a-column"></a>Recuperar la longitud o el estado de una columna  

Puede recuperar la longitud de una columna de longitud variable o el estado de una columna (para buscar DBSTATUS_S_ISNULL, por ejemplo):  
  
- Para obtener la longitud, use la macro COLUMN_ENTRY_LENGTH.  
  
- Para obtener el estado, use la macro COLUMN_ENTRY_STATUS.  
  
- Para obtener ambos, use COLUMN_ENTRY_LENGTH_STATUS, como se muestra a continuación.  
  
```cpp  
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
  
CTable<CAccessor<CProducts >> product;  
  
product.Open(session, "Product");  

while (product.MoveNext() == S_OK)  
{  
   // Check the product name isn't NULL before tracing it  
   if (product.nNameStatus == DBSTATUS_S_OK)  
      ATLTRACE("%s is %d characters\n", szName, nNameLength);  
}  
```  
  
Cuando usas `CDynamicAccessor`, la longitud y el estado se enlazan automáticamente. Para recuperar los valores de longitud y el estado, use la `GetLength` y `GetStatus` funciones miembro.  
  
## <a name="see-also"></a>Vea también  

[Trabajar con plantillas de consumidor OLE DB](../../data/oledb/working-with-ole-db-consumer-templates.md)