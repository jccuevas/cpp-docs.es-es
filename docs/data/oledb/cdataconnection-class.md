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
ms.openlocfilehash: 385445081f84f65ff7030466a238a5a96abd63be
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212073"
---
# <a name="cdataconnection-class"></a>CDataConnection (Clase)

Administra la conexión con el origen de datos.

## <a name="syntax"></a>Sintaxis

```cpp
class CDataConnection
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[CDataConnection](#cdataconnection)|Constructor. Crea una instancia e inicializa un objeto `CDataConnection`.|
|[Copy](#copy)|Crea una copia de una conexión de datos existente.|
|[Abrir](#open)|Abre una conexión a un origen de datos mediante una cadena de inicialización.|
|[OpenNewSession](#opennewsession)|Abre una nueva sesión en la conexión actual.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador BOOL](#op_bool)|Determina si la sesión actual está abierta o no.|
|[operator bool](#op_bool_ole)|Determina si la sesión actual está abierta o no.|
|[Operator CDataSource &](#op_cdata_amp)|Devuelve una referencia al objeto `CDataSource` contenido.|
|[operador CDataSource *](#op_cdata_star)|Devuelve un puntero al objeto `CDataSource` contenido.|
|[operador CSession &](#op_csession_amp)|Devuelve una referencia al objeto `CSession` contenido.|
|[operador CSession *](#op_csession_star)|Devuelve un puntero al objeto `CSession` contenido.|

## <a name="remarks"></a>Observaciones

`CDataConnection` es una clase útil para crear clientes porque encapsula los objetos necesarios (origen de datos y sesión) y parte del trabajo que debe realizar al conectarse a un origen de datos.

Sin `CDataConnection`, tiene que crear un objeto `CDataSource`, llamar a su método [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) y, a continuación, crear una instancia de un objeto [CSession](../../data/oledb/csession-class.md) , llamar a su método [Open](../../data/oledb/csession-open.md) y, a continuación, crear un objeto [CCommand](../../data/oledb/ccommand-class.md) y llamar a sus métodos `Open`*.

Con `CDataConnection`, solo tiene que crear un objeto de conexión, pasarle una cadena de inicialización y, a continuación, utilizar esa conexión para abrir comandos. Si piensa usar la conexión a la base de datos de forma repetida, es una buena idea mantener abierta la conexión y `CDataConnection` proporciona una forma cómoda de hacerlo.

> [!NOTE]
>  Si va a crear una aplicación de base de datos que necesita controlar varias sesiones, tendrá que usar [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnectioncdataconnection"></a><a name="cdataconnection"></a>CDataConnection:: CDataConnection

Crea una instancia e inicializa un objeto `CDataConnection`.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parámetros

*directorio*<br/>
de Referencia a una conexión de datos existente.

### <a name="remarks"></a>Observaciones

La primera invalidación crea un nuevo objeto `CDataConnection` con la configuración predeterminada.

La segunda invalidación crea un nuevo objeto `CDataConnection` con valores equivalentes al objeto de conexión de datos que especifique.

## <a name="cdataconnectioncopy"></a><a name="copy"></a>CDataConnection:: Copy

Crea una copia de una conexión de datos existente.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parámetros

*directorio*<br/>
de Referencia a una conexión de datos existente que se va a copiar.

## <a name="cdataconnectionopen"></a><a name="open"></a>CDataConnection:: Open

Abre una conexión a un origen de datos mediante una cadena de inicialización.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parámetros

*szInitString*<br/>
de Cadena de inicialización del origen de datos.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdataconnectionopennewsession"></a><a name="opennewsession"></a>CDataConnection:: OpenNewSession

Abre una nueva sesión con el origen de datos del objeto de conexión actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
[in/out] Referencia al nuevo objeto de sesión.

### <a name="remarks"></a>Observaciones

La nueva sesión utiliza el objeto de origen de datos contenido del objeto de conexión actual como su elemento primario y puede tener acceso a toda la información del origen de datos.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="cdataconnectionoperator-bool"></a><a name="op_bool"></a>CDataConnection:: Operator BOOL

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve el valor **bool** (MFC typedef). **True** significa que la sesión actual está abierta; **False** significa que la sesión actual está cerrada.

## <a name="cdataconnectionoperator-bool-ole-db"></a><a name="op_bool_ole"></a>CDataConnection:: Operator bool (OLE DB)

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Observaciones

Devuelve un **bool** valor booleanoC++ (tipo de datos). **true** significa que la sesión actual está abierta; **false** significa que la sesión actual está cerrada.

## <a name="cdataconnectionoperator-cdatasourceamp"></a><a name="op_cdata_amp"></a>CDataConnection:: Operator CDataSource&amp;

Devuelve una referencia al objeto `CDataSource` contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia al objeto `CDataSource` contenido, lo que le permite pasar un objeto `CDataConnection` en el que se espera una referencia `CDataSource`.

### <a name="example"></a>Ejemplo

Si tiene una función (como `func` siguiente) que toma una referencia `CDataSource`, puede usar `CDataSource&` para pasar un objeto `CDataConnection` en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="cdataconnectionoperator-cdatasource"></a><a name="op_cdata_star"></a>CDataConnection:: Operator CDataSource *

Devuelve un puntero al objeto `CDataSource` contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve un puntero al objeto `CDataSource` contenido, lo que le permite pasar un objeto `CDataConnection` en el que se espera un puntero `CDataSource`.

Vea [Operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) para obtener un ejemplo de uso.

## <a name="cdataconnectionoperator-csessionamp"></a><a name="op_csession_amp"></a>CDataConnection:: Operator CSession&amp;

Devuelve una referencia al objeto `CSession` contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve una referencia al objeto `CSession` contenido, lo que le permite pasar un objeto `CDataConnection` en el que se espera una referencia `CSession`.

### <a name="example"></a>Ejemplo

Si tiene una función (como `func` siguiente) que toma una referencia `CSession`, puede usar `CSession&` para pasar un objeto `CDataConnection` en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="cdataconnectionoperator-csession"></a><a name="op_csession_star"></a>CDataConnection:: Operator CSession *

Devuelve un puntero al objeto `CSession` contenido.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Observaciones

Este operador devuelve un puntero al objeto `CSession` contenido, lo que le permite pasar un objeto `CDataConnection` en el que se espera un puntero `CSession`.

### <a name="example"></a>Ejemplo

Vea [operador CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) para obtener un ejemplo de uso.

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
