---
title: CManualAccessor (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL::CManualAccessor
- ATL.CManualAccessor
- CManualAccessor
- ATL::CManualAccessor::AddBindEntry
- ATL.CManualAccessor.AddBindEntry
- CManualAccessor::AddBindEntry
- AddBindEntry
- CManualAccessor.AddBindEntry
- CManualAccessor::AddParameterEntry
- ATL.CManualAccessor.AddParameterEntry
- CManualAccessor.AddParameterEntry
- AddParameterEntry
- ATL::CManualAccessor::AddParameterEntry
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
- ATL::CManualAccessor::CreateParameterAccessor
- ATL.CManualAccessor.CreateParameterAccessor
- CManualAccessor.CreateParameterAccessor
- CreateParameterAccessor
- CManualAccessor::CreateParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CManualAccessor class
- AddBindEntry method
- AddParameterEntry method
- CreateAccessor method
- CreateParameterAccessor method
ms.assetid: a0088074-7135-465c-b228-69097a50b8cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 9b0cf71ce31d9f4d96d2064ebafd28b7ea5ff70d
ms.sourcegitcommit: b217daee32d3413cf33753d9b4dc35a0022b1bfa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39233475"
---
# <a name="cmanualaccessor-class"></a>CManualAccessor (Clase)
Representa un tipo de descriptor de acceso que ha diseñado para uso avanzado.  
  
## <a name="syntax"></a>Sintaxis

```cpp
class CManualAccessor : public CAccessorBase  
```  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldbcli.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[AddBindEntry](#addbindentry)|Agrega una entrada de enlace a las columnas de salida.|  
|[AddParameterEntry](#addparameterentry)|Agrega una entrada de parámetro para el descriptor de acceso de parámetro.|  
|[CreateAccessor](#createaccessor)|Asigna memoria para la columna de las estructuras de enlace e inicializa a los miembros de datos de columna.|  
|[CreateParameterAccessor](#createparameteraccessor)|Asigna memoria para el parámetro de enlace estructuras e inicializa a los miembros de datos de parámetro.|  
  
## <a name="remarks"></a>Comentarios  
 Uso de `CManualAccessor`, puede especificar el parámetro y el enlace de columna de salida por llamadas a funciones de tiempo de ejecución.  

## <a name="addbindentry"></a> CManualAccessor:: AddBindEntry
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
 Consulte [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) en el *referencia del programador OLE DB*.  
  
 *nOrdinal*  
 [in] Número de columna.  
  
 *wType*  
 [in] Tipo de datos.  
  
 *nColumnSize*  
 [in] Tamaño de columna en bytes.  
  
 *pData*  
 [in] Un puntero a la columna de datos almacenado en el búfer.  
  
 *pLength*  
 [in] Un puntero a la longitud de campo, si es necesario.  
  
 *pStatus*  
 [in] Un puntero a la variable esté enlazado con el estado de la columna, si es necesario.  
  
### <a name="remarks"></a>Comentarios  
 Para usar esta función, primero debe llamar a [CreateAccessor](../../data/oledb/cmanualaccessor-createaccessor.md). No se puede agregar más entradas que el número de columnas especificadas en `CreateAccessor`. 
  
## <a name="addparameterentry"></a> CManualAccessor:: AddParameterEntry
Agrega una entrada de parámetro a las estructuras de entrada de parámetro.  
  
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
 Consulte [DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx) en el *referencia del programador OLE DB*.  
  
 *nOrdinal*  
 [in] Número de parámetro.  
  
 *wType*  
 [in] Tipo de datos.  
  
 *nColumnSize*  
 [in] Tamaño de columna en bytes.  
  
 *pData*  
 [in] Un puntero a la columna de datos almacenado en el búfer.  
  
 *pLength*  
 [in] Un puntero a la longitud de campo, si es necesario.  
  
 *pStatus*  
 [in] Un puntero a la variable esté enlazado con el estado de la columna, si es necesario.  
  
 *eParamIO*  
 [in] Especifica si el parámetro que está asociado el enlace es un parámetro de entrada, entrada/salida o de salida.  
  
### <a name="remarks"></a>Comentarios  
 Para usar esta función, primero debe llamar a [CreateParameterAccessor](../../data/oledb/cmanualaccessor-createparameteraccessor.md). 

## <a name="createaccessor"></a> CManualAccessor:: CreateAccessor
Asigna memoria para la columna de las estructuras de enlace e inicializa a los miembros de datos de columna.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nBindEntries*  
 [in] Número de columnas. Este número debe coincidir con el número de llamadas a la [CManualAccessor:: AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) función.  
  
 *pBuffer*  
 [in] Un puntero al búfer donde se almacenan las columnas de salida.  
  
 *nBufferSize*  
 [in] El tamaño del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Llame a esta función antes de llamar a la `CManualAccessor::AddBindEntry` función.  

## <a name="createparameteraccessor"></a> CManualAccessor:: Createparameteraccessor
Asigna memoria para el parámetro de enlace estructuras e inicializa a los miembros de datos de parámetro.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateParameterAccessor(int nBindEntries,   
  void* pBuffer,   
   DBLENGTH nBufferSize) throw();  
```  
  
#### <a name="parameters"></a>Parámetros  
 *nBindEntries*  
 [in] Número de columnas.  
  
 *pBuffer*  
 [in] Un puntero al búfer donde se almacenan las columnas de entrada.  
  
 *nBufferSize*  
 [in] El tamaño del búfer en bytes.  
  
### <a name="return-value"></a>Valor devuelto  
 Uno de los valores HRESULT estándar.  
  
### <a name="remarks"></a>Comentarios  
 Debe llamar a esta función antes de llamar a [AddParameterEntry](../../data/oledb/cmanualaccessor-addparameterentry.md).

## <a name="see-also"></a>Vea también  
 [DBViewer](../../visual-cpp-samples.md)   
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor (clase)](../../data/oledb/caccessor-class.md)   
 [CDynamicAccessor (clase)](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)