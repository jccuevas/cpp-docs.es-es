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
ms.openlocfilehash: 94c7025185a24b07d5968157d49c856d4359b33a
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59021636"
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
|[CDataConnection](#cdataconnection)|Constructor. Crea una instancia e inicializa un `CDataConnection` objeto.|
|[Copiar](#copy)|Crea una copia de una conexión de datos existente.|
|[Abrir](#open)|Abre una conexión a un origen de datos mediante una cadena de inicialización.|
|[OpenNewSession](#opennewsession)|Se abre una nueva sesión en la conexión actual.|

### <a name="operators"></a>Operadores

|||
|-|-|
|[operador BOOL](#op_bool)|Determina si la sesión actual está abierta o no.|
|[operator bool](#op_bool_ole)|Determina si la sesión actual está abierta o no.|
|[operator CDataSource &](#op_cdata_amp)|Devuelve una referencia a la `CDataSource` objeto.|
|[operator CDataSource *](#op_cdata_star)|Devuelve un puntero para el objeto contenido `CDataSource` objeto.|
|[operador CSession &](#op_csession_amp)|Devuelve una referencia a la `CSession` objeto.|
|[operador CSession *](#op_csession_star)|Devuelve un puntero para el objeto contenido `CSession` objeto.|

## <a name="remarks"></a>Comentarios

`CDataConnection` es una clase útil para crear clientes porque encapsula los objetos necesarios (origen de datos y sesión) y parte del trabajo que debe hacer cuando se conecta a un origen de datos

Sin `CDataConnection`, tendrá que crear un `CDataSource` de objeto, llame a su [OpenFromInitializationString](../../data/oledb/cdatasource-openfrominitializationstring.md) método, a continuación, cree una instancia de un [CSession](../../data/oledb/csession-class.md) de objeto, llame a su [ Abra](../../data/oledb/csession-open.md) método, a continuación, cree un [CCommand](../../data/oledb/ccommand-class.md) objeto y llamar a su `Open`* métodos.

Con `CDataConnection`, basta con crear un objeto de conexión, le pasa una cadena de inicialización y luego usar esa conexión para abrir los comandos. Si planea usar la conexión a la base de datos varias veces, resulta una buena idea mantener abierta, la conexión y `CDataConnection` proporciona una manera cómoda de hacer eso.

> [!NOTE]
>  Si va a crear una aplicación de base de datos que necesita para administrar varias sesiones, deberá usar [OpenNewSession](../../data/oledb/cdataconnection-opennewsession.md).

## <a name="cdataconnection"></a> CDataConnection::CDataConnection

Crea una instancia e inicializa un `CDataConnection` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection();
CDataConnection(const CDataConnection &ds);
```

#### <a name="parameters"></a>Parámetros

*ds*<br/>
[in] Una referencia a una conexión de datos existente.

### <a name="remarks"></a>Comentarios

El primer reemplazo crea un nuevo `CDataConnection` objeto con la configuración predeterminada.

El segundo reemplazo crea un nuevo `CDataConnection` objeto con la configuración equivalente al objeto de conexión de datos que especifique.

## <a name="copy"></a> CDataConnection::Copy

Crea una copia de una conexión de datos existente.

### <a name="syntax"></a>Sintaxis

```cpp
CDataConnection& Copy(const CDataConnection & ds) throw();
```

#### <a name="parameters"></a>Parámetros

*ds*<br/>
[in] Una referencia a una conexión de datos existente para copiar.

## <a name="open"></a> CDataConnection::Open

Abre una conexión a un origen de datos mediante una cadena de inicialización.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(LPCOLESTR szInitString) throw();
```

#### <a name="parameters"></a>Parámetros

*szInitString*<br/>
[in] La cadena de inicialización del origen de datos.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="opennewsession"></a> CDataConnection::OpenNewSession

Se abre una nueva sesión con el origen de datos del objeto de conexión actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenNewSession(CSession & session) throw();
```

#### <a name="parameters"></a>Parámetros

*session*<br/>
[entrada/salida] Una referencia al objeto de sesión nuevo.

### <a name="remarks"></a>Comentarios

La nueva sesión usa el objeto de origen de datos independiente del objeto de conexión actual como su elemento primario y puede tener acceso a todos la misma información que el origen de datos.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="op_bool"></a> CDataConnection:: operator BOOL

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator BOOL() throw();
```

### <a name="remarks"></a>Comentarios

Devuelve **BOOL** valor (typedef MFC). **TRUE** significa que la sesión actual está abierta; **FALSE** significa que se cierra la sesión actual.

## <a name="op_bool_ole"></a> CDataConnection:: operator bool (OLE DB)

Determina si la sesión actual está abierta o no.

### <a name="syntax"></a>Sintaxis

```cpp
operator bool() throw();
```

### <a name="remarks"></a>Comentarios

Devuelve un **bool** valor (tipo de datos de C++). **True** significa que la sesión actual está abierta; **false** significa que se cierra la sesión actual.

## <a name="op_cdata_amp"></a> CDataConnection::operator CDataSource&amp;

Devuelve una referencia a la `CDataSource` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource&() throw();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve una referencia a la `CDataSource` objeto, lo que permite pasar un `CDataConnection` objeto donde un `CDataSource` referencia se espera.

### <a name="example"></a>Ejemplo

Si tiene una función (como `func` a continuación) que toma un `CDataSource` referencia, puede usar `CDataSource&` para pasar un `CDataConnection` objeto en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#3](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#4](../../data/oledb/codesnippet/cpp/cdataconnection-operator-cdatasource-amp_2.cpp)]

## <a name="op_cdata_star"></a> CDataConnection::operator CDataSource*

Devuelve un puntero para el objeto contenido `CDataSource` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CDataSource*() throw();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve un puntero para el objeto contenido `CDataSource` objeto, lo que permite pasar un `CDataConnection` objeto donde un `CDataSource` puntero se espera.

Consulte [operator CDataSource &](../../data/oledb/cdataconnection-operator-cdatasource-amp.md) para obtener un ejemplo de uso.

## <a name="op_csession_amp"></a> CDataConnection:: operator CSession&amp;

Devuelve una referencia a la `CSession` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession&();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve una referencia a la `CSession` objeto, lo que permite pasar un `CDataConnection` objeto donde un `CSession` referencia se espera.

### <a name="example"></a>Ejemplo

Si tiene una función (como `func` a continuación) que toma un `CSession` referencia, puede usar `CSession&` para pasar un `CDataConnection` objeto en su lugar.

[!code-cpp[NVC_OLEDB_Consumer#5](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_1.cpp)]

[!code-cpp[NVC_OLEDB_Consumer#6](../../data/oledb/codesnippet/cpp/cdataconnection-operator-csession-amp_2.cpp)]

## <a name="op_csession_star"></a> CDataConnection:: operator CSession *

Devuelve un puntero para el objeto contenido `CSession` objeto.

### <a name="syntax"></a>Sintaxis

```cpp
operator const CSession*() throw();
```

### <a name="remarks"></a>Comentarios

Este operador devuelve un puntero para el objeto contenido `CSession` objeto, lo que permite pasar un `CDataConnection` objeto donde un `CSession` puntero se espera.

### <a name="example"></a>Ejemplo

Consulte [operador CSession &](../../data/oledb/cdataconnection-operator-csession-amp.md) para obtener un ejemplo de uso.

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)