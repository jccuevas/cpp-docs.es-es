---
title: CDataSource (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL.CDataSource
- ATL::CDataSource
- CDataSource
- ATL::CDataSource::Close
- ATL.CDataSource.Close
- CDataSource::Close
- CDataSource.Close
- ATL::CDataSource::GetInitializationString
- CDataSource.GetInitializationString
- GetInitializationString
- CDataSource::GetInitializationString
- ATL.CDataSource.GetInitializationString
- CDataSource::GetProperties
- ATL.CDataSource.GetProperties
- CDataSource.GetProperties
- ATL::CDataSource::GetProperties
- ATL::CDataSource::GetProperty
- ATL.CDataSource.GetProperty
- CDataSource.GetProperty
- CDataSource::GetProperty
- ATL::CDataSource::Open
- ATL.CDataSource.Open
- CDataSource::Open
- CDataSource.Open
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
helpviewer_keywords:
- CDataSource class
- Close method
- GetInitializationString method
- GetProperties method
- GetProperty method
- Open method
- OpenFromFileName method
- OpenFromInitializationString method
- OpenWithPromptFileName method
- OpenWithServiceComponents method
ms.assetid: 99bf862c-9d5c-4117-9501-aa0e2672085c
ms.openlocfilehash: d97138b548a3e303898ee2bafde88af38aa78f40
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79545772"
---
# <a name="cdatasource-class"></a>CDataSource (Clase)

Corresponde a un objeto de origen de datos OLE DB, que representa una conexión a través de un proveedor a un origen de datos.

## <a name="syntax"></a>Sintaxis

```cpp
class CDataSource
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Close](#close)|Cierra la conexión.|
|[GetInitializationString](#getinitializationstring)|Recupera la cadena de inicialización del origen de datos que está abierta actualmente.|
|[GetProperties](#getproperties)|Obtiene los valores de las propiedades establecidas actualmente para el origen de datos conectado.|
|[GetProperty](#getproperty)|Obtiene el valor de una sola propiedad establecida actualmente para el origen de datos conectado.|
|[Abrir](#open)|Crea una conexión a un proveedor (origen de datos) mediante una `CLSID`, `ProgID`o un moniker `CEnumerator` proporcionado por el autor de la llamada.|
|[OpenFromFileName](#openfromfilename)|Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.|
|[OpenFromInitializationString](#openfrominitializationstring)|Abre el origen de datos especificado por una cadena de inicialización.|
|[OpenWithPromptFileName](#openwithpromptfilename)|Permite al usuario seleccionar un archivo de vínculo de datos creado previamente para abrir el origen de datos correspondiente.|
|[OpenWithServiceComponents](#openwithservicecomponents)|Abre un objeto de origen de datos mediante el cuadro de diálogo vínculo de datos.|

## <a name="remarks"></a>Observaciones

Se pueden crear una o varias sesiones de base de datos para una única conexión. Estas sesiones se representan mediante `CSession`. Debe llamar a [CDataSource:: Open](../../data/oledb/cdatasource-open.md) para abrir la conexión antes de crear una sesión con `CSession::Open`.

Para obtener un ejemplo de cómo usar `CDataSource`, vea el ejemplo [CatDB](../../overview/visual-cpp-samples.md) .

## <a name="cdatasourceclose"></a><a name="close"></a>CDataSource:: Close

Cierra la conexión liberando el puntero `m_spInit`.

### <a name="syntax"></a>Sintaxis

```cpp
void Close() throw();
```

## <a name="cdatasourcegetinitializationstring"></a><a name="getinitializationstring"></a>CDataSource:: GetInitializationString

Recupera la cadena de inicialización de un origen de datos que está abierto actualmente.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetInitializationString(BSTR* pInitializationString,
   bool bIncludePassword = false) throw();
```

#### <a name="parameters"></a>Parámetros

*pInitializationString*<br/>
enuncia Puntero a la cadena de inicialización.

*bIncludePassword*<br/>
de **true** si la cadena incluye una contraseña; en caso contrario, **false**.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

La cadena de inicialización resultante se puede usar para volver a abrir posteriormente esta conexión a un origen de datos.

## <a name="cdatasourcegetproperties"></a><a name="getproperties"></a>CDataSource:: GetProperties

Devuelve la información de propiedad solicitada para el objeto de origen de datos conectado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProperties(ULONG ulPropIDSets,
   constDBPROPIDSET* pPropIDSet,
   ULONG* pulPropertySets,
   DBPROPSET** ppPropsets) const throw();
```

#### <a name="parameters"></a>Parámetros

Vea [IDBProperties:: GetProperties](/previous-versions/windows/desktop/ms714344(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener una propiedad única, use [GetProperty](../../data/oledb/cdatasource-getproperty.md).

## <a name="cdatasourcegetproperty"></a><a name="getproperty"></a>CDataSource:: GetProperty

Devuelve el valor de una propiedad especificada para el objeto de origen de datos conectado.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetProperty(const GUID& guid,
   DBPROPID propid,
   VARIANT* pVariant) const throw();
```

#### <a name="parameters"></a>Parámetros

*guid*<br/>
de GUID que identifica el conjunto de propiedades para el que se va a devolver la propiedad.

*PROPID*<br/>
de IDENTIFICADOR de propiedad de la propiedad que se va a devolver.

*pVariant*<br/>
enuncia Puntero a la variante donde `GetProperty` devuelve el valor de la propiedad.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Para obtener varias propiedades, use [GetProperties](../../data/oledb/cdatasource-getproperties.md).

## <a name="cdatasourceopen"></a><a name="open"></a>CDataSource:: Open

Abre una conexión a un origen de datos mediante un moniker `CLSID`, `ProgID`o `CEnumerator` o solicita al usuario un cuadro de diálogo de localizador.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(const CLSID& clsid,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CLSID& clsid,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();HRESULT Open(LPCTSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();HRESULT Open(LPCTSTR szProgID,
   LPCTSTR pName,  LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(const CEnumerator& enumerator,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(const CEnumerator& enumerator,
   LPCTSTR pName,
   LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();

HRESULT Open(HWND hWnd = GetActiveWindow(),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_WIZARDSHEET) throw();

HRESULT Open(LPCWSTR szProgID,
   DBPROPSET* pPropSet = NULL,
   ULONG nPropertySets = 1) throw();

HRESULT Open(LPCSTR szProgID,
   LPCTSTR pName,LPCTSTR pUserName = NULL,
   LPCTSTR pPassword = NULL,
   long nInitMode = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*CLSID*<br/>
de `CLSID` del proveedor de datos.

*pPropSet*<br/>
de Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contiene las propiedades y los valores que se van a establecer. Vea [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK.

*nPropertySets*<br/>
de El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet* .

*pName*<br/>
[in] El nombre de la base de datos con la que se va a conectar.

*pUserName*<br/>
[in] El nombre de usuario.

*pPassword*<br/>
[in] La contraseña del usuario.

*nInitMode*<br/>
[in] El modo de inicialización de la base de datos. Vea [propiedades de inicialización](/previous-versions/windows/desktop/ms723127(v=vs.85))en la *Referencia del programador de OLE DB* en la Windows SDK para obtener una lista de los modos de inicialización válidos. Si *nInitMode* es cero, no se incluye ningún modo de inicialización en el conjunto de propiedades que se usa para abrir la conexión.

*szProgID*<br/>
[in] Un identificador de programa.

*enumerator*<br/>
de Un objeto [CEnumerator](../../data/oledb/cenumerator-class.md) que se usa para obtener un moniker para abrir la conexión cuando el autor de la llamada no especifica un `CLSID`.

*hWnd*<br/>
[in] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo. Al usar la sobrecarga de función que usa el parámetro *hWnd* , se invocarán automáticamente los componentes de servicio; Vea la sección Comentarios para obtener más información.

*dwPromptOptions*<br/>
[in] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar. Consulte los valores posibles en Msdasc.h.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

La sobrecarga del método que usa el parámetro *hWnd* abre un objeto de origen de datos con los componentes del servicio en oledb32. dll; este archivo DLL contiene la implementación de características de componentes de servicio como la agrupación de recursos, la inscripción automática de transacciones, etc. Para obtener más información, vea la referencia de OLE DB en la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

Las sobrecargas del método que no usan el parámetro *hWnd* abren un objeto de origen de datos sin utilizar los componentes del servicio en oledb32. dll. Un objeto [CDataSource](../../data/oledb/cdatasource-class.md) abierto con estas sobrecargas de función no podrá usar ninguna de las funciones de los componentes del servicio.

### <a name="example"></a>Ejemplo

En el código siguiente se muestra cómo abrir un origen de datos de Jet 4.0 con plantillas OLE DB. Trate el origen de datos de Jet como origen de datos OLE DB. Sin embargo, la llamada a `Open` necesita dos conjuntos de propiedades: uno para DBPROPSET_DBINIT y el otro para DBPROPSET_JETOLEDB_DBINIT, de modo que pueda establecer DBPROP_JETOLEDB_DATABASEPASSWORD.

[!code-cpp[NVC_OLEDB_Consumer#7](../../data/oledb/codesnippet/cpp/cdatasource-open_1.cpp)]

## <a name="cdatasourceopenfromfilename"></a><a name="openfromfilename"></a>CDataSource:: OpenFromFileName

Abre un origen de datos desde un archivo especificado por el nombre de archivo proporcionado por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();
```

#### <a name="parameters"></a>Parámetros

*szFileName*<br/>
[in] El nombre de un archivo, normalmente una conexión de origen de datos. Archivo (.UDL).

Para obtener más información acerca de los archivos de vínculo de datos (archivos. udl), consulte [información general](/previous-versions/windows/desktop/ms718102(v=vs.85)) sobre la API de vínculo de datos en el Windows SDK.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea la referencia de OLE DB en la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenfrominitializationstring"></a><a name="openfrominitializationstring"></a>CDataSource:: OpenFromInitializationString

Abre un origen de datos especificado por la cadena de inicialización proporcionada por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenFromInitializationString(LPCOLESTR szInitializationString,
   bool fPromptForInfo= false) throw();
```

#### <a name="parameters"></a>Parámetros

*szInitializationString*<br/>
de Cadena de inicialización.

*fPromptForInfo*<br/>
de Si este argumento se establece en **true**, `OpenFromInitializationString` establecerá la propiedad DBPROP_INIT_PROMPT en DBPROMPT_COMPLETEREQUIRED, que especifica que solo se solicitará al usuario si se necesita más información. Esto resulta útil en situaciones en las que la cadena de inicialización especifica una base de datos que requiere una contraseña, pero la cadena no contiene la contraseña. Al usuario se le solicitará una contraseña (o cualquier otra información que falte) al intentar conectarse a la base de datos.

El valor predeterminado es **false**, que especifica que nunca se solicitará al usuario (establece DBPROP_INIT_PROMPT en DBPROMPT_NOPROMPT).

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras.

## <a name="cdatasourceopenwithpromptfilename"></a><a name="openwithpromptfilename"></a>CDataSource:: OpenWithPromptFileName

Este método muestra al usuario un cuadro de diálogo y después abre un origen de datos mediante el archivo especificado por el usuario.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,
   LPCOLESTR szInitialDirectory = NULL) throw();
```

#### <a name="parameters"></a>Parámetros

*hWnd*<br/>
[in] Identificador de la ventana que va a ser el elemento primario del cuadro de diálogo.

*dwPromptOptions*<br/>
[in] Determina el estilo del cuadro de diálogo de localizador que se va a mostrar. Consulte los valores posibles en Msdasc.h.

*szInitialDirectory*<br/>
[in] El directorio inicial para mostrar en el cuadro de diálogo del localizador.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea la referencia de OLE DB en la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="cdatasourceopenwithservicecomponents"></a><a name="openwithservicecomponents"></a>CDataSource:: OpenWithServiceComponents

Abre un objeto de origen de datos usando los componentes del servicio en oledb32.dll.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);

HRESULT OpenWithServiceComponents (LPCSTR szProgID,
   DBPROPSET* pPropset = NULL,
   ULONG ulPropSets = 1);
```

#### <a name="parameters"></a>Parámetros

*CLSID*<br/>
de `CLSID` de un proveedor de datos.

*szProgID*<br/>
[in] Identificador de programa del proveedor de datos.

*pPropset*<br/>
de Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contiene las propiedades y los valores que se van a establecer. Vea [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK. Si el objeto de origen de datos se inicializa, las propiedades tienen que pertenecer al grupo de propiedades Data Source. Si se especifica la misma propiedad más de una vez en *pPropset*, el valor que se usa es específico del proveedor. Si *ulPropSets* es cero, este parámetro se omite.

*ulPropSets*<br/>
de El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet* . Si es cero, el proveedor omite *pPropset*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método abre un objeto de origen de datos con los componentes del servicio en oledb32.dll; este archivo DLL contiene la implementación de características de componentes de servicio, como la agrupación de recursos y la inscripción automática de transacciones, entre otras. Para obtener más información, vea la referencia de OLE DB en la [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643(v=vs.85)).

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)