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
ms.openlocfilehash: 52c7e2ce5acdd2df33e2a6422535a337f0a43aec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368627"
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
El tipo de clase `CDynamicParameterAccessor`de `CDynamicStringAccessor`descriptor `CEnumeratorAccessor`de acceso (como , , o ) que desea que utilice el comando. El valor `CNoAccessor`predeterminado es , que especifica que la clase no admite parámetros ni columnas de salida.

*TRowset*<br/>
El tipo de clase `CArrayRowset` de `CNoRowset`conjunto de filas (como o ) que desea que utilice el comando. El valor predeterminado es `CRowset`.

*TMultiple*<br/>
Para utilizar un comando OLE DB que puede devolver varios resultados, especifique [CMultipleResults](../../data/oledb/cmultipleresults-class.md). De lo contrario, utilice [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Para obtener más información, consulte [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Cerrar](#close)|Cierra el comando actual.|
|[GetNextResult](#getnextresult)|Obtiene el siguiente resultado cuando se utilizan varios conjuntos de resultados.|
|[Abrir](#open)|Ejecuta y, opcionalmente, enlaza el comando.|

### <a name="inherited-methods"></a>Métodos heredados

|||
|-|-|
|[Crear](#create)|Crea un nuevo comando para la sesión especificada y, a continuación, establece el texto del comando.|
|[CreateCommand](#createcommand)|Crea un nuevo comando.|
|[GetParameterInfo](#getparameterinfo)|Obtiene una lista de los parámetros del comando, sus nombres y sus tipos.|
|[Preparación](#prepare)|Valida y optimiza el comando actual.|
|[ReleaseCommand](#releasecommand)|Libera el descriptor de acceso de parámetro si es necesario y, a continuación, suelta el comando.|
|[SetParameterInfo](#setparameterinfo)|Especifica el tipo nativo de cada parámetro de comando.|
|[Unprepare](#unprepare)|Descarta el plan de ejecución de comandos actual.|

## <a name="remarks"></a>Observaciones

Utilice esta clase cuando necesite realizar una operación basada en parámetros o ejecutar un comando. Si solo necesita abrir un conjunto de filas simple, utilice [CTable](../../data/oledb/ctable-class.md) en su lugar.

La clase de descriptor de acceso que está utilizando determina el método de enlace de parámetros y datos.

Tenga en cuenta que no puede usar procedimientos almacenados con el proveedor OLE DB para Jet porque ese proveedor no admite procedimientos almacenados (solo se permiten constantes en cadenas de consulta).

## <a name="ccommandclose"></a><a name="close"></a>CCommand::Cerrar

Libera el conjunto de filas de descriptor de acceso asociado al comando.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Observaciones

Un comando utiliza un conjunto de filas, un descriptor de acceso de conjunto de resultados y (opcionalmente) un descriptor de acceso de parámetro (a diferencia de las tablas, que no admiten parámetros y no necesitan un descriptor de acceso de parámetro).

Al ejecutar un comando, debe `Close` llamar a ambos y [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) después del comando.

Cuando desee ejecutar el mismo comando repetidamente, debe liberar `Close` cada `Execute`descriptor de acceso del conjunto de resultados llamando antes de llamar a . Al final de la serie, debe liberar `ReleaseCommand`el descriptor de acceso de parámetro llamando a . Otro escenario común es llamar a un procedimiento almacenado que tiene parámetros de salida. En muchos proveedores (como el proveedor OLE DB para SQL Server) los valores de parámetro de salida no serán accesibles hasta que cierre el descriptor de acceso del conjunto de resultados. Llame `Close` para cerrar el conjunto de filas devuelto y el descriptor de acceso del conjunto de resultados, pero no el descriptor de acceso de parámetro, lo que le permite recuperar los valores de parámetro de salida.

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo se puede llamar a `Close` y `ReleaseCommand` cuando se ejecuta el mismo comando varias veces.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="ccommandgetnextresult"></a><a name="getnextresult"></a>CCommand::GetNextResult

Obtiene el siguiente conjunto de resultados si hay uno disponible.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parámetros

*pulRowsAfectado*<br/>
[entrada/salida] Puntero a la memoria donde se devuelve el recuento de filas afectadas por un comando.

*bBind*<br/>
[en] Especifica si se enlazar el comando automáticamente después de ejecutarse. El valor predeterminado es **true**, lo que hace que el comando se enlaza automáticamente. Establecer *bBind* en **false** impide el enlace automático del comando para que pueda enlazar manualmente. (El enlace manual es de particular interés para los usuarios de OLAP.)

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Si un conjunto de resultados se ha capturado previamente, esta función libera el conjunto de resultados anterior y desenlaza las columnas. Si *bBind* es **true**, enlaza las nuevas columnas.

Debe llamar a esta función solo si ha `CCommand` especificado varios resultados estableciendo el parámetro de plantilla *TMultiple*=`CMultipleResults`.

## <a name="ccommandopen"></a><a name="open"></a>CCommand::Abierto

Ejecuta y, opcionalmente, enlaza el comando.

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

*Sesión*<br/>
[en] La sesión en la que se ejecutará el comando.

*wszCommand*<br/>
[en] El comando que se va a ejecutar, pasado como una cadena Unicode. Puede ser NULL `CAccessor`cuando se usa , en cuyo caso el comando se recuperará del valor pasado a la macro [DEFINE_COMMAND.](../../data/oledb/define-command.md) Consulte [ICommand::Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) en la *referencia del programador OLE DB* para obtener más información.

*szCommand*<br/>
[en] Igual que *wszCommand* excepto que este parámetro toma una cadena de comandos ANSI. La cuarta forma de este método puede tomar un valor NULL. Consulte "Comentarios" más adelante en este tema para obtener más información.

*pPropSet*<br/>
[en] Puntero a una matriz de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) que contienen propiedades y valores que se van a establecer. Consulte [Conjuntos](/previous-versions/windows/desktop/ms713696(v=vs.85)) de propiedades y grupos de propiedades en la *referencia del programador OLE DB* en el Windows SDK.

*pRowsAfectado*<br/>
[entrada/salida] Puntero a la memoria donde se devuelve el recuento de filas afectadas por un comando. Si * \*pRowsAffected* es NULL, no se devuelve ningún recuento de filas. De `Open` lo contrario, establece * \*pRowsAffected* según las siguientes condiciones:

|Si|Entonces|
|--------|----------|
|El `cParamSets` elemento `pParams` de es mayor que 1|pRowsAffected representa el número total de filas afectadas por todos los conjuntos de parámetros especificados en la ejecución. * \**|
|El número de filas afectadas no está disponible|pRowsAffected se establece en -1. * \**|
|El comando no actualiza, elimina ni inserta filas|pRowsAffected es indefinido. * \**|

*guidCommand*<br/>
[en] GUID que especifica la sintaxis y las reglas generales que el proveedor usará para analizar el texto del comando. Vea [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) y [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) en la *referencia del programador OLE DB* para obtener más información.

*bBind*<br/>
[en] Especifica si se enlazar el comando automáticamente después de ejecutarse. El valor predeterminado es **true**, lo que hace que el comando se enlaza automáticamente. Establecer *bBind* en **false** impide el enlace automático del comando para que pueda enlazar manualmente. (El enlace manual es de particular interés para los usuarios de OLAP.)

*ulPropSets*<br/>
[en] El número de estructuras [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasadas en el argumento *pPropSet.*

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Las tres primeras formas de `Open` tomar una sesión, crear un comando y ejecutar el comando, enlazar cualquier parámetro según sea necesario.

La primera `Open` forma de toma una cadena de comandos Unicode y no tiene ningún valor predeterminado.

La segunda `Open` forma de toma una cadena de comandos ANSI y ningún valor predeterminado (proporcionado para la compatibilidad con versiones anteriores con aplicaciones ANSI existentes).

La tercera `Open` forma de permite que la cadena de comandos sea NULL, debido al tipo **int** con un valor predeterminado de NULL. Se proporciona para `Open(session, NULL);` `Open(session);` llamar o porque NULL es de tipo **int**. Esta versión requiere y afirma que el parámetro **int** es NULL.

Utilice la cuarta `Open` forma de cuando ya haya creado un comando y desee realizar una sola [preparación](../../data/oledb/ccommand-prepare.md) y varias ejecuciones.

> [!NOTE]
> `Open`llamadas `Execute`, que `GetNextResult`a su vez llama .

## <a name="ccommandcreate"></a><a name="create"></a>CCommand::Crear

Llama a [CCommand::CreateCommand](../../data/oledb/ccommand-createcommand.md) para crear un comando para la sesión especificada y, a continuación, llama a [ICommandText::SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) para especificar el texto del comando.

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

*Sesión*<br/>
[en] Una sesión en la que crear el comando.

*wszCommand*<br/>
[en] Un puntero al texto Unicode de la cadena de comandos.

*szCommand*<br/>
[en] Puntero al texto ANSI de la cadena de comandos.

*guidCommand*<br/>
[en] GUID que especifica la sintaxis y las reglas generales que el proveedor usará para analizar el texto del comando. Para obtener una descripción de dialectos, vea [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

La primera `Create` forma de toma una cadena de comandos Unicode. La segunda `Create` forma de toma una cadena de comandos ANSI (proporcionada para la compatibilidad con versiones anteriores con aplicaciones ANSI existentes).

## <a name="ccommandcreatecommand"></a><a name="createcommand"></a>CCommand::CreateCommand

Crea un nuevo comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parámetros

*Sesión*<br/>
[en] Objeto `CSession` que se va a asociar al nuevo comando.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método crea un comando mediante el objeto de sesión especificado.

## <a name="ccommandgetparameterinfo"></a><a name="getparameterinfo"></a>CCommand::GetParameterInfo

Obtiene una lista de los parámetros del comando, sus nombres y sus tipos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandWithParameters::GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="ccommandprepare"></a><a name="prepare"></a>CCommand::Prepare

Valida y optimiza el comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*cExpectedRuns*<br/>
[en] El número de veces que espera ejecutar el comando.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método ajusta el método OLE DB [ICommandPrepare::Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="ccommandreleasecommand"></a><a name="releasecommand"></a>CCommand::ReleaseCommand

Libera el descriptor de acceso de parámetro y, a continuación, libera el propio comando.

### <a name="syntax"></a>Sintaxis

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Observaciones

`ReleaseCommand`se utiliza junto `Close`con . Consulte [Cerrar](../../data/oledb/ccommand-close.md) para obtener más información sobre el uso.

## <a name="ccommandsetparameterinfo"></a><a name="setparameterinfo"></a>CCommand::SetParameterInfo

Especifica el tipo nativo de cada parámetro de comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parámetros

Vea [ICommandWithParameters::SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) en la *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="ccommandunprepare"></a><a name="unprepare"></a>CCommand::Unprepare

Descarta el plan de ejecución de comandos actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Observaciones

Este método ajusta el método OLE DB [ICommandPrepare::Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)
