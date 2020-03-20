---
title: CManualAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
ms.openlocfilehash: 80c8f94a417c700f86159de53bd53e4011f78d71
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79546072"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor (Clase)

Representa un tipo de descriptor de acceso diseñado para uso avanzado.

## <a name="syntax"></a>Sintaxis

```cpp
class CManualAccessor : public CAccessorBase
```

## <a name="requirements"></a>Requisitos

**Encabezado:** atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[AddBindEntry](#addbindentry)|Agrega una entrada de enlace a las columnas de salida.|
|[AddParameterEntry](#addparameterentry)|Agrega una entrada de parámetro al descriptor de acceso del parámetro.|
|[CreateAccessor](#createaccessor)|Asigna memoria a las estructuras de enlace de columna e inicializa los miembros de datos de columna.|
|[CreateParameterAccessor](#createparameteraccessor)|Asigna memoria para las estructuras de enlace de parámetro e inicializa los miembros de datos de parámetro.|

## <a name="remarks"></a>Observaciones

Con `CManualAccessor`, puede especificar el parámetro y el enlace de la columna de salida mediante llamadas a funciones en tiempo de ejecución.

## <a name="cmanualaccessoraddbindentry"></a><a name="addbindentry"></a>CManualAccessor:: AddBindEntry

Agrega una entrada de enlace a las columnas de salida.

### <a name="syntax"></a>Sintaxis

```cpp
void AddBindEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL) throw ();
```

#### <a name="parameters"></a>Parámetros

Vea [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *Referencia del programador de OLE DB*.

*nOrdinal*<br/>
de Número de columna.

*wType*<br/>
de Tipo de datos.

*nColumnSize*<br/>
de Tamaño de la columna en bytes.

*pData*<br/>
de Puntero a los datos de columna almacenados en el búfer.

*pLength*<br/>
de Puntero a la longitud del campo, si es necesario.

*pStatus*<br/>
de Puntero a la variable que se va a enlazar al estado de la columna, si es necesario.

### <a name="remarks"></a>Observaciones

Para usar esta función, primero debe llamar a [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). No se pueden agregar más entradas que el número de columnas especificado en `CreateAccessor`.

## <a name="cmanualaccessoraddparameterentry"></a><a name="addparameterentry"></a>CManualAccessor:: AddParameterEntry

Agrega una entrada de parámetro a las estructuras de entrada de parámetros.

### <a name="syntax"></a>Sintaxis

```cpp
void AddParameterEntry(DBORDINAL nOrdinal,
   DBTYPE wType,  DBLENGTH nColumnSize,
   void* pData,
   void* pLength = NULL,
   void* pStatus = NULL,
   DBPARAMIO eParamIO = DBPARAMIO_INPUT) throw ();
```

#### <a name="parameters"></a>Parámetros

Vea [DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85)) en la *Referencia del programador de OLE DB*.

*nOrdinal*<br/>
de Número de parámetro.

*wType*<br/>
de Tipo de datos.

*nColumnSize*<br/>
de Tamaño de la columna en bytes.

*pData*<br/>
de Puntero a los datos de columna almacenados en el búfer.

*pLength*<br/>
de Puntero a la longitud del campo, si es necesario.

*pStatus*<br/>
de Puntero a la variable que se va a enlazar al estado de la columna, si es necesario.

*eParamIO*<br/>
de Especifica si el parámetro con el que está asociado el enlace es un parámetro de entrada, de entrada/salida o de salida.

### <a name="remarks"></a>Observaciones

Para usar esta función, primero debe llamar a [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md).

## <a name="cmanualaccessorcreateaccessor"></a><a name="createaccessor"></a>CManualAccessor:: CreateAccessor

Asigna memoria a las estructuras de enlace de columna e inicializa los miembros de datos de columna.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateAccessor(int nBindEntries,
  void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parámetros

*nBindEntries*<br/>
de Número de columnas. Este número debe coincidir con el número de llamadas a la función [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) .

*pBuffer*<br/>
de Puntero al búfer donde se almacenan las columnas de salida.

*nBufferSize*<br/>
de Tamaño del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Llame a esta función antes de llamar a la función `CManualAccessor::AddBindEntry`.

## <a name="cmanualaccessorcreateparameteraccessor"></a><a name="createparameteraccessor"></a>CManualAccessor:: CreateParameterAccessor

Asigna memoria para las estructuras de enlace de parámetro e inicializa los miembros de datos de parámetro.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT CreateParameterAccessor(int nBindEntries,
   void* pBuffer,
   DBLENGTH nBufferSize) throw();
```

#### <a name="parameters"></a>Parámetros

*nBindEntries*<br/>
de Número de columnas.

*pBuffer*<br/>
de Puntero al búfer donde se almacenan las columnas de entrada.

*nBufferSize*<br/>
de Tamaño del búfer en bytes.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

Debe llamar a esta función antes de llamar a [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Consulte también

[DBViewer](../../overview/visual-cpp-samples.md)<br/>
[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)