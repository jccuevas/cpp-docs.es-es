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
ms.openlocfilehash: 6ba56143beb3411734899839a46ab42992dfa4d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231000"
---
# <a name="cdynamicstringaccessor-class"></a>CDynamicStringAccessor (Clase)

Permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente de la base de datos).

## <a name="syntax"></a>Sintaxis

```cpp
template< typename BaseType, DBTYPEENUM OleDbType >
class CDynamicStringAccessorT : public CDynamicAccessor
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetString](#getstring)|Recupera los datos de la columna especificada como una cadena.|
|[SetString](#setstring)|Establece los datos de la columna especificada como una cadena.|

## <a name="remarks"></a>Comentarios

Mientras [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) solicita datos en el formato nativo notificado por el proveedor, `CDynamicStringAccessor` solicita que el proveedor recupere todos los datos que se obtiene acceso desde el almacén de datos como datos de cadena. Esto es especialmente útil para tareas sencillas que no requieren el cálculo de valores en el almacén de datos, como mostrar o imprimir el contenido del almacén de datos.

No importa el tipo de datos de columna en el almacén de datos nativo. siempre que el proveedor puede admitir la conversión de datos, proporcionará los datos en formato de cadena. Si el proveedor no admite la conversión de tipo de datos nativo a una cadena (que no es habitual), la llamada de solicitud devolverá el valor de éxito DB_S_ERRORSOCCURED y el estado de la columna correspondiente indicará un problema de conversión con DBSTATUS_E_CANTCONVERTVALUE.

Use `CDynamicStringAccessor` métodos para obtener información de columna. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución.

La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener datos desde el búfer mediante [GetString](../../data/oledb/cdynamicstringaccessor-getstring.md), o lo almacena en el búfer mediante [SetString](../../data/oledb/cdynamicstringaccessor-setstring.md).

Para obtener una explicación y ejemplos del uso de las clases de descriptor de acceso dinámico, consulte [utilizar descriptores de acceso dinámico](../../data/oledb/using-dynamic-accessors.md).

## <a name="getstring"></a> CDynamicStringAccessor::GetString

Recupera los datos de la columna especificada como una cadena.

### <a name="syntax"></a>Sintaxis

```cpp
BaseType* GetString(DBORDINAL nColumn) const throw();

BaseType* GetString(const CHAR* pColumnName) const throw();

BaseType* GetString(const WCHAR* pColumnName) const throw();
```

#### <a name="parameters"></a>Parámetros

*nColumn*<br/>
[in] El número de columna. Números de columna empiezan por 1. Un valor de 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

### <a name="return-value"></a>Valor devuelto

Recupera un puntero al valor de cadena de la columna especificada. El valor es de tipo `BaseType`, que será **CHAR** o **WCHAR** dependiendo de si se define _UNICODE o no. Devuelve NULL si no se encuentra la columna especificada.

### <a name="remarks"></a>Comentarios

La segunda invalidación formulario toma el nombre de columna como una cadena ANSI. La tercera invalidar formulario toma el nombre de columna como una cadena Unicode.

## <a name="setstring"></a> CDynamicStringAccessor::SetString

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
[in] El número de columna. Números de columna empiezan por 1. El valor especial 0 hace referencia a la columna de marcador, si existe.

*pColumnName*<br/>
[in] Un puntero a una cadena de caracteres que contiene el nombre de columna.

*data*<br/>
[in] Un puntero a los datos de cadena se escriban en la columna especificada.

### <a name="return-value"></a>Valor devuelto

Un puntero al valor de cadena que se va a establecer la columna especificada. El valor es de tipo `BaseType`, que será **CHAR** o **WCHAR** dependiendo de si se define _UNICODE o no.

### <a name="remarks"></a>Comentarios

El segundo invalidar formulario toma el nombre de columna como una cadena ANSI y la tercera invalidar formulario toma el nombre de columna como una cadena Unicode.

Si _SECURE_ATL se define con un valor distinto de cero, se generará un error de aserción en tiempo de ejecución si la entrada *datos* cadena es mayor que la longitud máxima permitida de la columna de datos que se hace referencia. En caso contrario, la cadena de entrada se truncará si es mayor que la longitud máxima permitida.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessorA (Clase)](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW (Clase)](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CXMLAccessor (Clase)](../../data/oledb/cxmlaccessor-class.md)