---
title: CCommand (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CCommand
- CCommand
- ATL.CCommand
- CCommand.Close
- CCommand::Close
- CCommand.Create
- CCommand::Create
- CCommand.CreateCommand
- CreateCommand
- CCommand::CreateCommand
- ATL::CCommand::GetNextResult
- CCommand::GetNextResult
- GetNextResult
- CCommand.GetNextResult
- ATL.CCommand.GetNextResult
- GetParameterInfo
- CCommand.GetParameterInfo
- CCommand::GetParameterInfo
- ATL.CCommand.Open
- ATL::CCommand::Open
- CCommand.Open
- CCommand::Open
- CCommand.Prepare
- CCommand::Prepare
- Prepare
- CCommand.ReleaseCommand
- ReleaseCommand
- CCommand::ReleaseCommand
- SetParameterInfo
- CCommand.SetParameterInfo
- CCommand::SetParameterInfo
- Unprepare
- CCommand.Unprepare
- CCommand::Unprepare
helpviewer_keywords:
- CCommand class
- Close method
- Create method [C++]
- CreateCommand method
- GetNextResult method
- GetParameterInfo method
- Open method
- Prepare method
- ReleaseCommand method
- SetParameterInfo method
- Unprepare method
ms.assetid: 0760bfc5-b9ee-4aee-8e54-31bd78714d3a
ms.openlocfilehash: 5da843405cfec4d1d571a3140f132513d8b068ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212087"
---
# <a name="ccommand-class"></a>CCommand (Clase)

Proporciona métodos para establecer y ejecutar un comando.

## <a name="syntax"></a>Sintaxis

```cpp
template <class TAccessor = CNoAccessor,
   template <typename T> class TRowset = CRowset,
   class TMultiple = CNoMultipleResults>
class CCommand :
   public CAccessorRowset <TAccessor, TRowset>,
   public CCommandBase,
   public TMultiple
```

### <a name="parameters"></a>Parámetros

*TAccessor*<br/>
El tipo de clase de descriptor de acceso (como `CDynamicParameterAccessor`, `CDynamicStringAccessor`o `CEnumeratorAccessor`) que desea que use el comando. El valor predeterminado es `CNoAccessor`, que especifica que la clase no admite parámetros ni columnas de salida.

*TRowset*<br/>
El tipo de clase de conjunto de filas (como `CArrayRowset` o `CNoRowset`) que desea que use el comando. El valor predeterminado es `CRowset`.

*TMultiple*<br/>
Para usar un comando OLE DB que puede devolver varios resultados, especifique [cmultipleresults (](../../data/oledb/cmultipleresults-class.md). De lo contrario, use [cnomultipleresults (](../../data/oledb/cnomultipleresults-class.md). Para obtener más información, consulte [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[Close](#close)|Cierra el comando actual.|
|[GetNextResult](#getnextresult)|Captura el siguiente resultado cuando se usan varios conjuntos de resultados.|
|[Abrir](#open)|Ejecuta y, de forma opcional, enlaza el comando.|

### <a name="inherited-methods"></a>Métodos heredados

|||
|-|-|
|[Creación](#create)|Crea un nuevo comando para la sesión especificada y, a continuación, establece el texto del comando.|
|[CreateCommand](#createcommand)|Crea un nuevo comando.|
|[GetParameterInfo](#getparameterinfo)|Obtiene una lista de los parámetros del comando, sus nombres y sus tipos.|
|[Preparación](#prepare)|Valida y optimiza el comando actual.|
|[ReleaseCommand](#releasecommand)|Libera el descriptor de acceso del parámetro si es necesario y, a continuación, libera el comando.|
|[SetParameterInfo](#setparameterinfo)|Especifica el tipo nativo de cada parámetro de comando.|
|[Unprepare](#unprepare)|Descarta el plan de ejecución de comandos actual.|

## <a name="remarks"></a>Observaciones

Utilice esta clase cuando necesite realizar una operación basada en parámetros o ejecutar un comando. Si solo necesita abrir un conjunto de filas simple, use [CTable](../../data/oledb/ctable-class.md) en su lugar.

La clase de descriptor de acceso que está usando determina el método de enlace de datos y parámetros.

Tenga en cuenta que no puede utilizar procedimientos almacenados con el proveedor de OLE DB para Jet porque ese proveedor no admite procedimientos almacenados (solo se permiten constantes en las cadenas de consulta).

## <a name="ccommandclose"></a><a name="close"></a>CCommand:: Close

Libera el conjunto de filas de descriptor de acceso asociado al comando.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

Un comando usa un conjunto de filas, un descriptor de acceso de conjunto de resultados y, opcionalmente, un descriptor de acceso de parámetro (a diferencia de las tablas, que no admiten parámetros y no necesitan un descriptor de acceso de parámetro).

Al ejecutar un comando, debe llamar a `Close` y [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) después del comando.

Si desea ejecutar el mismo comando repetidamente, debe liberar cada descriptor de acceso del conjunto de resultados llamando a `Close` antes de llamar a `Execute`. Al final de la serie, debe liberar el descriptor de acceso de parámetro llamando a `ReleaseCommand`. Otro escenario común es llamar a un procedimiento almacenado que tenga parámetros de salida. En muchos proveedores (como el proveedor de OLE DB para SQL Server), los valores de los parámetros de salida no serán accesibles hasta que se cierre el descriptor de acceso del conjunto de resultados. Llame a `Close` para cerrar el descriptor de acceso devuelto y del conjunto de resultados, pero no el descriptor de acceso del parámetro, lo que le permite recuperar los valores del parámetro de salida.

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo se puede llamar a `Close` y `ReleaseCommand` cuando se ejecuta el mismo comando varias veces.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand:: GetNextResult

Captura el siguiente conjunto de resultados, si hay alguno disponible.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parámetros

*pulRowsAffected*<br/>
[in/out] Puntero a la memoria en la que se devuelve el recuento de filas afectadas por un comando.

*bBind*<br/>
de Especifica si se debe enlazar el comando automáticamente después de ejecutarse. El valor predeterminado es **true**, que hace que el comando se enlace automáticamente. Si se establece *bBind* en **false** , se impide el enlace automático del comando para que se pueda enlazar manualmente. (El enlace manual es de especial interés para los usuarios de OLAP).

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si se ha capturado previamente un conjunto de resultados, esta función libera el conjunto de resultados anterior y desenlaza las columnas. Si *bBind* es **true**, enlaza las nuevas columnas.

Solo debe llamar a esta función si ha especificado varios resultados estableciendo el parámetro de plantilla `CCommand` *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand:: Open

Ejecuta y, de forma opcional, enlaza el comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT Open(const CSession& session,
   LPCWSTR wszCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   LPCSTR szCommand,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(const CSession& session,
   INT szCommand = NULL,
   DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   REFGUID guidCommand = DBGUID_DEFAULT,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();

HRESULT Open(DBPROPSET *pPropSet = NULL,
   DBROWCOUNT* pRowsAffected = NULL,
   bool bBind = true,
   ULONG ulPropSets = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
de Sesión en la que se va a ejecutar el comando.

*wszCommand*<br/>
de Comando que se va a ejecutar, pasado como una cadena Unicode. Puede ser NULL cuando se usa `CAccessor`, en cuyo caso el comando se recuperará del valor pasado a la macro [DEFINE_COMMAND](../../data/oledb/define-command.md) . Vea [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

*szCommand*<br/>
de Igual que *wszCommand* , salvo que este parámetro toma una cadena de comando ANSI. El cuarto formulario de este método puede tomar un valor NULL. Vea la sección "Comentarios" más adelante en este tema para obtener más información.

*pPropSet*<br/>
de Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contiene las propiedades y los valores que se van a establecer. Vea [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en la *Referencia del programador de OLE DB* en el Windows SDK.

*pRowsAffected*<br/>
[in/out] Puntero a la memoria en la que se devuelve el recuento de filas afectadas por un comando. Si *\*pRowsAffected* es null, no se devuelve ningún recuento de filas. De lo contrario, `Open` establece *\*pRowsAffected* según las condiciones siguientes:

|Si|Entonces|
|--------|----------|
|El elemento `cParamSets` de `pParams` es mayor que 1|*\*pRowsAffected* representa el número total de filas afectadas por todos los conjuntos de parámetros especificados en la ejecución.|
|El número de filas afectadas no está disponible|*\*pRowsAffected* se establece en-1.|
|El comando no actualiza, elimina o inserta filas|*\*pRowsAffected* no está definido.|

*guidCommand*<br/>
de GUID que especifica la sintaxis y las reglas generales que el proveedor debe usar para analizar el texto del comando. Consulte [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) y [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) en la *Referencia del programador de OLE DB* para obtener más información.

*bBind*<br/>
de Especifica si se debe enlazar el comando automáticamente después de ejecutarse. El valor predeterminado es **true**, que hace que el comando se enlace automáticamente. Si se establece *bBind* en **false** , se impide el enlace automático del comando para que se pueda enlazar manualmente. (El enlace manual es de especial interés para los usuarios de OLAP).

*ulPropSets*<br/>
de El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet* .

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Las tres primeras formas de `Open` tomar una sesión, crear un comando y ejecutar el comando, enlazando los parámetros según sea necesario.

La primera forma de `Open` toma una cadena de comandos Unicode y no tiene ningún valor predeterminado.

La segunda forma de `Open` toma una cadena de comandos ANSI y ningún valor predeterminado (se proporciona por compatibilidad con versiones anteriores de las aplicaciones ANSI existentes).

La tercera forma de `Open` permite que la cadena de comando sea nula, debido al tipo **int** con un valor predeterminado de NULL. Se proporciona para llamar a `Open(session, NULL);` o `Open(session);` porque NULL es de tipo **int**. Esta versión requiere y valida que el parámetro **int** sea NULL.

Use el cuarto formulario de `Open` cuando ya haya creado un comando y desee realizar una sola [preparación](../../data/oledb/ccommand-prepare.md) y varias ejecuciones.

> [!NOTE]
>  `Open` llama a `Execute`, que a su vez llama a `GetNextResult`.

## <a name="ccommandcreate"></a><a name="create"></a>CCommand:: Create

Llama a [CCommand:: CreateCommand](../../data/oledb/ccommand-createcommand.md) para crear un comando para la sesión especificada y, a continuación, llama a [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) para especificar el texto del comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Create(const CSession& session,
   LPCWSTR wszCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();

HRESULT CCommandBase::Create(const CSession& session,
   LPCSTR szCommand,
   REFGUID guidCommand = DBGUID_DEFAULT) throw ();
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
de Sesión en la que se va a crear el comando.

*wszCommand*<br/>
de Puntero al texto Unicode de la cadena de comandos.

*szCommand*<br/>
de Puntero al texto ANSI de la cadena de comandos.

*guidCommand*<br/>
de GUID que especifica la sintaxis y las reglas generales que el proveedor debe usar para analizar el texto del comando. Para obtener una descripción de los dialectos, vea [ICommandText:: GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

La primera forma de `Create` toma una cadena de comandos Unicode. La segunda forma de `Create` toma una cadena de comandos ANSI (se proporciona por compatibilidad con versiones anteriores de las aplicaciones ANSI existentes).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand:: CreateCommand

Crea un nuevo comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parámetros

*sesión*<br/>
de Objeto `CSession` que se va a asociar al nuevo comando.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método crea un comando mediante el objeto de sesión especificado.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand:: GetParameterInfo

Obtiene una lista de los parámetros del comando, sus nombres y sus tipos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::P redondear

Valida y optimiza el comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*cExpectedRuns*<br/>
de Número de veces que se espera ejecutar el comando.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método ajusta el método OLE DB [ICommandPrepare::P reparet](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand:: ReleaseCommand

Libera el descriptor de acceso del parámetro y, a continuación, libera el propio comando.

### <a name="syntax"></a>Sintaxis

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Observaciones

`ReleaseCommand` se utiliza junto con `Close`. Vea [cerrar](../../data/oledb/ccommand-close.md) para obtener detalles de uso.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand:: SetParameterInfo

Especifica el tipo nativo de cada parámetro de comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) en la *Referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand:: Unprepare

Descarta el plan de ejecución de comandos actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Valor devuelto

HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método ajusta el método OLE DB [ICommandPrepare:: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
