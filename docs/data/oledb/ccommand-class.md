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
ms.openlocfilehash: 406a78ff1958d565fcc74781f6a63d4784f48bfc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176101"
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
El tipo de clase de descriptor de acceso (como `CDynamicParameterAccessor`, `CDynamicStringAccessor`, o `CEnumeratorAccessor`) que desea que el comando para usar. El valor predeterminado es `CNoAccessor`, que especifica que la clase no admite parámetros o columnas de salida.

*TRowset*<br/>
El tipo de clase de conjunto de filas (como `CArrayRowset` o `CNoRowset`) que desea que el comando para usar. De manera predeterminada, es `CRowset`.

*TMultiple*<br/>
Para usar un comando de OLE DB que puede devolver varios resultados, especifique [CMultipleResults](../../data/oledb/cmultipleresults-class.md). En caso contrario, use [CNoMultipleResults](../../data/oledb/cnomultipleresults-class.md). Para obtener más información, consulte [IMultipleResults](/previous-versions/windows/desktop/ms721289(v=vs.85)).

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[Cerrar](#close)|Cierra el comando actual.|
|[GetNextResult](#getnextresult)|Recupera el resultado siguiente al utilizar conjuntos de resultados múltiples.|
|[Abrir](#open)|Se ejecuta y, opcionalmente, enlaza el comando.|

### <a name="inherited-methods"></a>Métodos heredados

|||
|-|-|
|[Crear](#create)|Crea un nuevo comando para la sesión especificada, a continuación, Establece el texto del comando.|
|[CreateCommand](#createcommand)|Crea un nuevo comando.|
|[GetParameterInfo](#getparameterinfo)|Obtiene una lista de parámetros del comando, sus nombres y sus tipos.|
|[Preparar](#prepare)|Valida y optimiza el comando actual.|
|[ReleaseCommand](#releasecommand)|Libera el descriptor de acceso del parámetro si es necesario, a continuación, libera el comando.|
|[SetParameterInfo](#setparameterinfo)|Especifica el tipo nativo de cada parámetro de comando.|
|[Unprepare](#unprepare)|Descarta el plan de ejecución del comando actual.|

## <a name="remarks"></a>Comentarios

Utilice esta clase cuando necesite realizar una operación basada en parámetros o ejecutar un comando. Si simplemente tiene que abrir un conjunto de filas simple, use [CTable](../../data/oledb/ctable-class.md) en su lugar.

La clase de descriptor de acceso que usa determina el método de enlace de parámetros y datos.

Tenga en cuenta que no puede utilizar procedimientos almacenados con el proveedor OLE DB para Jet dado que el proveedor no admite procedimientos (solo se permiten constantes en las cadenas de consulta).

## <a name="close"></a> CCommand::Close

Libera el conjunto de filas de descriptor de acceso asociada con el comando.

### <a name="syntax"></a>Sintaxis

```cpp
void Close();
```

### <a name="remarks"></a>Comentarios

Un comando usa un conjunto de filas, descriptor de acceso de conjunto de resultados y (opcionalmente) un descriptor de acceso de parámetro (a diferencia de las tablas, que no admiten parámetros y no es necesario un descriptor de acceso de parámetro).

Cuando se ejecuta un comando, debe llamar a ambos `Close` y [ReleaseCommand](../../data/oledb/ccommand-releasecommand.md) después del comando.

Cuando desea ejecutar varias veces el mismo comando, debe liberar cada descriptor de acceso del conjunto de resultados mediante una llamada a `Close` antes de llamar a `Execute`. Al final de la serie, debe liberar el descriptor de acceso de parámetro mediante una llamada a `ReleaseCommand`. Otro escenario común es una llamada a un procedimiento almacenado con parámetros de salida. En muchos proveedores (por ejemplo, el proveedor OLE DB para SQL Server) los valores de parámetro de salida no será accesibles hasta que cierre el descriptor de acceso del conjunto de resultados. Llame a `Close` para cerrar el conjunto de filas devuelto y el descriptor de acceso de conjunto de resultados, pero no el descriptor de acceso de parámetro, lo que le permite recuperar los valores de parámetro de salida.

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo se puede llamar a `Close` y `ReleaseCommand` cuando se ejecuta el mismo comando varias veces.

[!code-cpp[NVC_OLEDB_Consumer#2](../../data/oledb/codesnippet/cpp/ccommand-close_1.cpp)]

## <a name="getnextresult"></a> CCommand::GetNextResult

Recupera el siguiente conjunto de resultados si está disponible.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetNextResult(DBROWCOUNT* pulRowsAffected,
   bool bBind = true) throw();
```

#### <a name="parameters"></a>Parámetros

*pulRowsAffected*<br/>
[entrada/salida] Un puntero a memoria que se devuelve el recuento de filas afectadas por un comando.

*bBind*<br/>
[in] Especifica si se debe enlazar el comando automáticamente después de que se está ejecutando. El valor predeterminado es **true**, lo que hace que el comando que se enlazará automáticamente. Establecer *bBind* a **false** impide que el enlace automático del comando para que pueda enlazar manualmente. (Enlace manual es de especial interés para los usuarios OLAP).

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Si un conjunto de resultados se han obtenido anteriormente, esta función libera el conjunto de resultados anterior y desenlaza las columnas. Si *bBind* es **true**, enlaza las columnas nuevas.

Debe llamar a esta función solo si ha especificado varios resultados estableciendo la `CCommand` parámetro de plantilla *TMultiple*=`CMultipleResults`.

## <a name="open"></a> CCommand::Open

Se ejecuta y, opcionalmente, enlaza el comando.

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

*session*<br/>
[in] La sesión en el que se va a ejecutar el comando.

*wszCommand*<br/>
[in] El comando se ejecute, se pasa como una cadena Unicode. Puede ser NULL cuando se usa `CAccessor`, en cuyo caso el comando se recuperan desde el valor pasado a la [DEFINE_COMMAND](../../data/oledb/define-command.md) macro. Consulte [ICommand:: Execute](/previous-versions/windows/desktop/ms718095(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

*szCommand*<br/>
[in] Igual que *wszCommand* , salvo que este parámetro toma una cadena de comando de ANSI. La cuarta forma de este método puede tomar un valor NULL. Vea "Comentarios" más adelante en este tema para obtener más información.

*pPropSet*<br/>
[in] Un puntero a una matriz de [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) estructuras que contienen las propiedades y valores que desea establecer. Consulte [conjuntos de propiedades y grupos de propiedades](/previous-versions/windows/desktop/ms713696(v=vs.85)) en el *referencia del programador OLE DB* en el SDK de Windows.

*pRowsAffected*<br/>
[entrada/salida] Un puntero a memoria que se devuelve el recuento de filas afectadas por un comando. Si  *\*pRowsAffected* es NULL, no se devuelve ningún recuento de filas. En caso contrario, `Open` establece  *\*pRowsAffected* según las condiciones siguientes:

|Si|A continuación|
|--------|----------|
|El `cParamSets` elemento de `pParams` es mayor que 1|*\*pRowsAffected* representa el número total de filas afectadas por todos los conjuntos de parámetros especificados en la ejecución.|
|El número de filas afectadas no está disponible|*\*pRowsAffected* se establece en -1.|
|El comando no actualizar, eliminar o insertar filas|*\*pRowsAffected* es indefinido.|

*guidCommand*<br/>
[in] Un GUID que especifica la sintaxis y las reglas generales para el proveedor debe usar al analizar el texto del comando. Consulte [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) y [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) en el *referencia del programador de OLE DB* para obtener más información.

*bBind*<br/>
[in] Especifica si se debe enlazar el comando automáticamente después de que se está ejecutando. El valor predeterminado es **true**, lo que hace que el comando que se enlazará automáticamente. Establecer *bBind* a **false** impide que el enlace automático del comando para que pueda enlazar manualmente. (Enlace manual es de especial interés para los usuarios OLAP).

*ulPropSets*<br/>
[in] El número de [DBPROPSET](/previous-versions/windows/desktop/ms714367(v=vs.85)) pasan las estructuras en el *pPropSet* argumento.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Los tres primeros formularios de `Open` tomar una sesión, crear un comando y ejecute el comando, los parámetros de enlace según sea necesario.

El primer formulario del `Open` toma una cadena de comando de Unicode y no tiene ningún valor predeterminado.

La segunda forma de `Open` toma una cadena de comando de ANSI y ningún valor predeterminado (proporcionado por motivos de compatibilidad con las aplicaciones existentes de ANSI).

La tercera forma de `Open` permite que la cadena de comando sea NULL, debido a un tipo **int** con un valor predeterminado es null. Se proporciona para llamar a `Open(session, NULL);` o `Open(session);` porque es NULL de tipo **int**. Esta versión requiere y declara que el **int** parámetro sea NULL.

Usar la forma del cuarta `Open` cuando ya ha creado un comando y desea realizar una sola [preparar](../../data/oledb/ccommand-prepare.md) y varias ejecuciones.

> [!NOTE]
>  `Open` las llamadas `Execute`, que a su vez llama a `GetNextResult`.

## <a name="create"></a> CCommand::Create

Las llamadas [CCommand:: CreateCommand](../../data/oledb/ccommand-createcommand.md) para crear un comando para la sesión especificada, a continuación, llama a [ICommandText:: SetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) para especificar el texto del comando.

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

*session*<br/>
[in] Una sesión en el que se va a crear el comando.

*wszCommand*<br/>
[in] Un puntero al texto Unicode de la cadena de comandos.

*szCommand*<br/>
[in] Un puntero al texto ANSI de la cadena de comandos.

*guidCommand*<br/>
[in] Un GUID que especifica la sintaxis y las reglas generales para el proveedor debe usar al analizar el texto del comando. Para obtener una descripción de dialectos, consulte [ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) en el *referencia del programador de OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

El primer formulario del `Create` toma una cadena de comando de Unicode. La segunda forma de `Create` toma una cadena de comando de ANSI (proporcionada por motivos de compatibilidad con las aplicaciones existentes de ANSI).

## <a name="createcommand"></a> CCommand::CreateCommand

Crea un nuevo comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::CreateCommand(const CSession& session) throw ();
```

#### <a name="parameters"></a>Parámetros

*session*<br/>
[in] Un `CSession` objeto va a asociar con el nuevo comando.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método crea un comando mediante el objeto de sesión especificado.

## <a name="getparameterinfo"></a> CCommand::GetParameterInfo

Obtiene una lista de parámetros del comando, sus nombres y sus tipos.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::GetParameterInfo(DB_UPARAMS* pParams,
   DBPARAMINFO** ppParamInfo,
   OLECHAR** ppNamesBuffer) throw ();
```

#### <a name="parameters"></a>Parámetros

Consulte [ICommandWithParameters:: GetParameterInfo](/previous-versions/windows/desktop/ms714917(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="prepare"></a> CCommand:: Prepare

Valida y optimiza el comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Prepare(ULONG cExpectedRuns = 0) throw();
```

#### <a name="parameters"></a>Parámetros

*cExpectedRuns*<br/>
[in] El número de veces que se espera para ejecutar el comando.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método ajusta el método OLE DB [ICommandPrepare:: Prepare](/previous-versions/windows/desktop/ms718370(v=vs.85)).

## <a name="releasecommand"></a> CCommand::ReleaseCommand

Libera el descriptor de acceso de parámetro, a continuación, libera el propio comando.

### <a name="syntax"></a>Sintaxis

```cpp
void CCommandBase::ReleaseCommand() throw();
```

### <a name="remarks"></a>Comentarios

`ReleaseCommand` se usa junto con `Close`. Consulte [cerrar](../../data/oledb/ccommand-close.md) para obtener detalles de uso.

## <a name="setparameterinfo"></a> CCommand::SetParameterInfo

Especifica el tipo nativo de cada parámetro de comando.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::SetParameterInfo(DB_UPARAMS ulParams,
   const DBORDINAL* pOrdinals,
   const DBPARAMBINDINFO* pParamInfo) throw();
```

#### <a name="parameters"></a>Parámetros

Consulte [ICommandWithParameters:: SetParameterInfo](/previous-versions/windows/desktop/ms725393(v=vs.85)) en el *referencia del programador OLE DB*.

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

## <a name="unprepare"></a> CCommand::Unprepare

Descarta el plan de ejecución del comando actual.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CCommandBase::Unprepare() throw();
```

### <a name="return-value"></a>Valor devuelto

Un HRESULT estándar.

### <a name="remarks"></a>Comentarios

Este método ajusta el método OLE DB [ICommandPrepare:: Unprepare](/previous-versions/windows/desktop/ms719635(v=vs.85)).

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)