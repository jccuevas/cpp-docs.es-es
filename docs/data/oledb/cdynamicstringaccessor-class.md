---
title: CDynamicStringAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessor
- CDynamicStringAccessor.GetString
- CDynamicStringAccessor::GetString
- CDynamicStringAccessor::SetString
- CDynamicStringAccessor.SetString
helpviewer_keywords:
- CDynamicStringAccessor class
- GetString method
- SetString method
ms.assetid: 138dc4de-c7c3-478c-863e-431e48249027
ms.openlocfilehash: a0590bc015c5487315b8cbd38f0baf91eb3082cc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211876"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor (Clase)

Permite tener acceso a un origen de datos cuando no se conoce el esquema de la base de datos (la estructura subyacente de la base de datos).

## <a name="syntax"></a>Sintaxis

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetString](#getstring)|Recupera los datos de la columna especificada como una cadena.|
|[SetString](#setstring)|Establece los datos de la columna especificada como una cadena.|

## <a name="remarks"></a>Observaciones

Mientras que [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) solicita datos en el formato nativo que el proveedor ha indicado, `CDynamicStringAccessor` solicita que el proveedor recupere todos los datos a los que se tiene acceso desde el almacén de datos como datos de cadena. Esto es especialmente útil para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como la visualización o la impresión del contenido del almacén de datos.

No importa el tipo nativo de datos de columna en el almacén de datos; siempre que el proveedor pueda admitir la conversión de datos, proporcionará los datos en formato de cadena. Si el proveedor no admite la conversión del tipo de datos nativo a una cadena (lo que no es habitual), la llamada que realiza la solicitud devolverá el valor correcto DB_S_ERRORSOCCURED y el estado de la columna correspondiente indicará un problema de conversión con DBSTATUS_E_CANTCONVERTVALUE.

Use métodos `CDynamicStringAccessor` para obtener información de columnas. Esta información de columna se usa para crear un descriptor de acceso dinámicamente en tiempo de ejecución.

La información de la columna se almacena en un búfer creado y administrado por esta clase. Obtenga datos del búfer mediante [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md)o almacénelos en el búfer mediante [setString](../../data/oledb/cdynamicstringaccessor-setstring.md).

Para obtener una explicación y ejemplos del uso de las clases de descriptor de acceso dinámico, vea usar descriptores de [acceso dinámicos](../../data/oledb/using-dynamic-accessors.md).

## <a name="cdynamicstringaccessorgetstring"></a><a name="getstring"></a>CDynamicStringAccessor:: GetString

Recupera los datos de la columna especificada como una cadena.

### <a name="syntax"></a>Sintaxis

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de la columna.

### <a name="return-value"></a>Valor devuelto

Puntero al valor de cadena recuperado de la columna especificada. El valor es de tipo `BaseType`, que será **Char** o **WCHAR** dependiendo de si _UNICODE está definido o no. Devuelve NULL si no se encuentra la columna especificada.

### <a name="remarks"></a>Observaciones

El segundo formulario de invalidación toma el nombre de la columna como una cadena ANSI. El tercer formulario de invalidación toma el nombre de la columna como una cadena Unicode.

## <a name="cdynamicstringaccessorsetstring"></a><a name="setstring"></a>CDynamicStringAccessor:: SetString

Establece los datos de la columna especificada como una cadena.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT SetString(DBORDINAL nColumn,
   BaseType* data) throw();

HRESULT SetString(const CHAR* pColumnName,
   BaseType* data) throw();

HRESULT SetString(const WCHAR* pColumnName,
   BaseType* data) throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
de El número de columna. Los números de columna empiezan por 1. El valor especial de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
de Puntero a una cadena de caracteres que contiene el nombre de la columna.

*data*<br/>
de Puntero a los datos de cadena que se van a escribir en la columna especificada.

### <a name="return-value"></a>Valor devuelto

Puntero al valor de cadena en el que se va a establecer la columna especificada. El valor es de tipo `BaseType`, que será **Char** o **WCHAR** dependiendo de si _UNICODE está definido o no.

### <a name="remarks"></a>Observaciones

El segundo formulario de invalidación toma el nombre de columna como una cadena ANSI y el tercer formulario de invalidación toma el nombre de columna como una cadena Unicode.

Si se define _SECURE_ATL para tener un valor distinto de cero, se generará un error de aserción en tiempo de ejecución si la cadena de *datos* de entrada es mayor que la longitud máxima permitida de la columna de datos a la que se hace referencia. De lo contrario, la cadena de entrada se truncará si es mayor que la longitud máxima permitida.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA (Clase)](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW (Clase)](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor (Clase)](../../data/oledb/cxmlaccessor-class.md)
