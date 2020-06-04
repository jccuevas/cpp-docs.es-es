---
title: CDataConnection (Clase)
ms.date: 03/27/2019
f1_keywords:
- ATL::CDataConnection
- ATL.CDataConnection
- CDataConnection
- CDataConnection.CDataConnection
- ATL.CDataConnection.CDataConnection
- CDataConnection::CDataConnection
- ATL::CDataConnection::CDataConnection
- CDataConnection.Copy
- ATL.CDataConnection.Copy
- ATL::CDataConnection::Copy
- CDataConnection::Copy
- CDataConnection.Open
- ATL.CDataConnection.Open
- CDataConnection::Open
- ATL::CDataConnection::Open
- CDataConnection.OpenNewSession
- ATL.CDataConnection.OpenNewSession
- ATL::CDataConnection::OpenNewSession
- OpenNewSession
- CDataConnection::OpenNewSession
- CDataConnection::operatorBOOL
- ATL::CDataConnection::operatorBOOL
- CDataConnection.operatorBOOL
- ATL.CDataConnection.operatorBOOL
- CDataSource&
- CDataConnection.operatorCDataSource&
- operatorCDataSource&
- CDataConnection::operatorCDataSource&
- CDataSource*
- CDataConnection::operatorCDataSource*
- CDataConnection.operatorCDataSource*
- operatorCDataSource*
- CSession&
- CDataConnection::operatorCSession&
- CDataConnection.operatorCSession&
- operatorCSession&
- CDataConnection.operatorCSession*
- CDataConnection::operatorCSession*
- operatorCSession*
- CSession*
helpviewer_keywords:
- CDataConnection class
- CDataConnection class, constructor
- Copy method
- Open method
- OpenNewSession method
- BOOL operator
- operator bool
- BOOL operator
- operator bool
- CDataSource& operator
- operator & (CDataSource)
- CDataSource* operator
- operator * (CDataSource)
- operator CSession&
- CSession& operator
- operator CSession*
- CSession* operator
ms.assetid: 77432d85-4e20-49ec-a0b0-142137828471
ms.openlocfilehash: fe954e218a099fa7956748904a4baa89f741c52f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368613"
---
# <a name="cdataconnection-class"></a>CDataConnection (Clase)

Administra la conexión con el origen de datos.

## <a name="syntax"></a>Sintaxis

```cpp
class CDataConnection
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CDataConnection](#cdataconnection)|Constructor. Crea una instancia `CDataConnection` e inicializa un objeto.|
|[Copiar](#copy)|Crea una copia de una conexión de datos existente.|
|[Abrir](#open)|Abre una conexión a un origen de datos mediante una cadena de inicialización.|
|[OpenNewSession](#opennewsession)|Abre una nueva sesión en la conexión actual.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador BOOL](#op_bool)|Determina si la sesión actual está abierta o no.|
|[operador bool](#op_bool_ole)|Determina si la sesión actual está abierta o no.|
|[operador CDataSource&](#op_cdata_amp)|Devuelve una referencia al `CDataSource` objeto contenido.|
|[operador CDataSource*](#op_cdata_star)|Devuelve un puntero al `CDataSource` objeto contenido.|
|[operador CSession&](#op_csession_amp)|Devuelve una referencia al `CSession` objeto contenido.|
|[operador CSession*](#op_csession_star)|Devuelve un puntero al `CSession` objeto contenido.|

## <a name="remarks"></a>Observaciones

`CDataConnection`es una clase útil para crear clientes porque encapsula los objetos necesarios (origen de datos y sesión) y parte del trabajo que debe realizar al conectarse a un origen de datos

Sin `CDataConnection`, tiene `CDataSource` que crear un objeto, llamar a su [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) método, a continuación, crear una instancia `Open`de un [CSession](../../data/oledb/csession-class.md) objeto, llamar a su [Open](../../data/oledb/csession-open.md) método, a continuación, crear un [CCommand](../../data/oledb/ccommand-class.md) objeto y llamar a su * métodos.

Con `CDataConnection`, solo necesita crear un objeto de conexión, pasarle una cadena de inicialización y, a continuación, utilizar esa conexión para abrir comandos. Si planea usar la conexión a la base de datos repetidamente, es `CDataConnection` una buena idea mantener la conexión abierta y proporciona una manera conveniente de hacerlo.

> [!NOTE]
> Si va a crear una aplicación de base de datos que necesita controlar varias sesiones, deberá usar [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection::CDataConnection

Crea una instancia `CDataConnection` e inicializa un objeto.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parámetros

*Ds*<br/>
[en] Una referencia a una conexión de datos existente.

### <a name="remarks"></a>Observaciones

La primera invalidación crea un nuevo `CDataConnection` objeto con la configuración predeterminada.

La segunda invalidación crea un nuevo `CDataConnection` objeto con valores equivalentes al objeto de conexión de datos que especifique.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection::Copy

Crea una copia de una conexión de datos existente.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parámetros

*Ds*<br/>
[en] Una referencia a una conexión de datos existente para copiar.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection::Open

Abre una conexión a un origen de datos mediante una cadena de inicialización.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parámetros

*szInitString*<br/>
[en] La cadena de inicialización para el origen de datos.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection::OpenNewSession

Abre una nueva sesión con el origen de datos del objeto de conexión actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parámetros

*Sesión*<br/>
[entrada/salida] Una referencia al nuevo objeto de sesión.

### <a name="remarks"></a>Observaciones

La nueva sesión utiliza el objeto de origen de datos contenido del objeto de conexión actual como su elemento primario y puede tener acceso a toda la misma información que el origen de datos.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection::operator BOOL

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve el valor **BOOL** (MFC typedef). **TRUE** significa que la sesión actual está abierta; **FALSE** significa que la sesión actual está cerrada.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection::operator bool (OLE DB)

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve un valor **bool** (tipo de datos C++). **true** significa que la sesión actual está abierta; **false** significa que la sesión actual está cerrada.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection::operator CDataSource&amp;

Devuelve una referencia al `CDataSource` objeto contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia `CDataSource` al objeto contenido, `CDataConnection` lo `CDataSource` que le permite pasar un objeto donde se espera una referencia.

### <a name="example"></a>Ejemplo

Si tiene una función `func` (como la `CDataSource` siguiente) que `CDataSource&` toma `CDataConnection` una referencia, puede utilizar para pasar un objeto en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection::operator CDataSource*

Devuelve un puntero al `CDataSource` objeto contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve un puntero `CDataSource` al objeto contenido, `CDataConnection` lo `CDataSource` que le permite pasar un objeto donde se espera un puntero.

Consulte [el operador CDataSource&](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) para obtener un ejemplo de uso.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection::operator CSession&amp;

Devuelve una referencia al `CSession` objeto contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia `CSession` al objeto contenido, `CDataConnection` lo `CSession` que le permite pasar un objeto donde se espera una referencia.

### <a name="example"></a>Ejemplo

Si tiene una función `func` (como la `CSession` siguiente) que `CSession&` toma `CDataConnection` una referencia, puede utilizar para pasar un objeto en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection::operator CSession*

Devuelve un puntero al `CSession` objeto contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve un puntero `CSession` al objeto contenido, `CDataConnection` lo `CSession` que le permite pasar un objeto donde se espera un puntero.

### <a name="example"></a>Ejemplo

Consulte [el operador CSession&](../../data/oledb/cdataconnection-operator-csession-amp.md) para obtener un ejemplo de uso.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
