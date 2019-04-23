---
title: Métodos generados por el Asistente para consumidores
ms.date: 11/04/2016
helpviewer_keywords:
- OpenAll method
- attribute-injected classes and methods
- wizard-generated classes and methods
- OLE DB consumers, wizard-generated classes and methods
- methods [C++], OLE DB Consumer Wizard-generated
- CloseDataSource method
- consumer wizard-generated classes and methods
- OpenDataSource method
- CloseAll method
- OpenRowset method
- GetRowsetProperties method
ms.assetid: d80ee51c-8bb3-4dca-8760-5808e0fb47b4
ms.openlocfilehash: 60ca0af25a0556c4a3d42d91ba3b0c52daa5f530
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59034246"
---
# <a name="consumer-wizard-generated-methods"></a>Métodos generados por el Asistente para consumidores

El **el Asistente para consumidores OLE DB ATL** y **MFC Application Wizard** generar ciertas funciones de los cuales debe tener en cuenta. Algunos métodos se implementan de forma diferente en los proyectos con atributos, por lo que hay algunas advertencias; cada caso se trata más adelante. Para obtener información acerca de cómo ver código insertado, vea [Depurar código insertado](/visualstudio/debugger/how-to-debug-injected-code).

- `OpenAll` se abre el origen de datos, conjuntos de filas y activa los marcadores si están disponibles.

- `CloseAll` abrir todos los conjuntos de filas se cierra y libera todas las ejecuciones de comandos.

- `OpenRowset` llama a `OpenAll` para abrir el conjunto de filas o los conjuntos de filas del consumidor.

- `GetRowsetProperties` Recupera un puntero a la propiedad del conjunto de filas con las propiedades que se pueden establecer.

- `OpenDataSource` Abre el origen de datos mediante la cadena de inicialización especificada en el **propiedades de vínculo de datos** cuadro de diálogo.

- `CloseDataSource` cierra el origen de datos de una manera adecuada.

## <a name="openall-and-closeall"></a>OpenAll y CloseAll

```cpp
HRESULT OpenAll();

void CloseAll();
```

El ejemplo siguiente muestra cómo se puede llamar a `OpenAll` y `CloseAll` cuando se ejecuta el mismo comando varias veces. Comparar el código de ejemplo [CCommand:: Close](../../data/oledb/ccommand-close.md), que muestra una variación que llama a `Close` y `ReleaseCommand` en lugar de `CloseAll`.

```cpp
int main(int argc, char* argv[])
{
   HRESULT hr;

   hr = CoInitialize(NULL);

   CCustOrdersDetail rs;      // Your CCommand-derived class
   rs.m_OrderID = 10248;      // Open order 10248
   hr = rs.OpenAll();         // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the first command execution
   rs.Close();

   rs.m_OrderID = 10249;      // Open order 10249 (a new order)
   hr = rs.Open();            // (Open also executes the command)
   hr = rs.MoveFirst();         // Move to the first row and print it
   printf( "Name: %s, Unit Price: %d, Quantity: %d, Discount %d, Extended Price %d\n", rs.m_ProductName, rs.m_UnitPrice.int64, rs.m_Quantity, rs.m_Discount, rs.m_ExtendedPrice.int64 );

   // Close the second command execution;
   // Instead of rs.CloseAll() you could call
   // rs.Close() and rs.ReleaseCommand():
   rs.CloseAll();

   CoUninitialize();
   return 0;
}
```

### <a name="remarks"></a>Comentarios

Si define un `HasBookmark` método, el `OpenAll` código establece el `DBPROP_IRowsetLocate` propiedad; Asegúrese de que sólo hacerlo si su proveedor admite esa propiedad.

## <a name="openrowset"></a>OpenRowset

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET* pPropSet = NULL)
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand = NULL);
```

`OpenAll` llama a este método para abrir el conjunto de filas en el consumidor. Normalmente, no es necesario llamar a `OpenRowset` a menos que desee trabajar con varios orígenes de datos/sesiones/conjuntos de filas. `OpenRowset` se declara en el archivo de encabezado de clase de comando o una tabla:

```cpp
// OLE DB Template version:
HRESULT OpenRowset(DBPROPSET *pPropSet = NULL)
{
   HRESULT hr = Open(m_session, NULL, pPropSet);
   #ifdef _DEBUG
   if(FAILED(hr))
      AtlTraceErrorRecords(hr);
   #endif
   return hr;
}
```

Los atributos implementan este método de manera diferente. Esta versión toma un objeto de sesión y una cadena de comando cuyo valor predeterminado es la cadena de comando especificada en db_command, aunque puede pasar otro diferente. Si define un `HasBookmark` método, el `OpenRowset` código establece el `DBPROP_IRowsetLocate` propiedad; Asegúrese de que sólo hacerlo si su proveedor admite esa propiedad.

```cpp
// Attribute-injected version:
HRESULT OpenRowset(const CSession& session, LPCWSTR szCommand=NULL)
{

   DBPROPSET *pPropSet = NULL;
   CDBPropSet propset(DBPROPSET_ROWSET);
   __if_exists(HasBookmark)

   {
      propset.AddProperty(DBPROP_IRowsetLocate, true);
      pPropSet= &propset;
      }
...
}
```

## <a name="getrowsetproperties"></a>GetRowsetProperties

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet);
```

Este método recupera un puntero al conjunto de propiedades del conjunto de filas; Puede usar este puntero para establecer propiedades tales como `DBPROP_IRowsetChange`. `GetRowsetProperties` se usa en la clase de registro de usuario como se indica a continuación. Puede modificar este código para establecer las propiedades del conjunto de filas adicionales:

```cpp
void GetRowsetProperties(CDBPropSet* pPropSet)
{
   pPropSet->AddProperty(DBPROP_CANFETCHBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_CANSCROLLBACKWARDS, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_IRowsetChange, true, DBPROPOPTIONS_OPTIONAL);
   pPropSet->AddProperty(DBPROP_UPDATABILITY, DBPROPVAL_UP_CHANGE | DBPROPVAL_UP_INSERT | DBPROPVAL_UP_DELETE);
}
```

### <a name="remarks"></a>Comentarios

No debe definir un global `GetRowsetProperties` método porque podrían entrar en conflicto con el definido por el asistente. Este es un método generado por el asistente que se obtiene con proyectos de plantillas y atributos. los atributos no insertan este código.

## <a name="opendatasource-and-closedatasource"></a>OpenDataSource y CloseDataSource

```cpp
HRESULT OpenDataSource();

void CloseDataSource();
```

### <a name="remarks"></a>Comentarios

El asistente define los métodos `OpenDataSource` y `CloseDataSource`; `OpenDataSource` llamadas [CDataSource:: OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md).

## <a name="see-also"></a>Vea también

[Crear un consumidor OLE DB mediante un asistente](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)