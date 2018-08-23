---
title: CUtlProps (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CUtlProps
- CUtlProps::GetPropValue
- CUtlProps.GetPropValue
- GetPropValue
- CUtlProps::IsValidValue
- CUtlProps.IsValidValue
- IsValidValue
- CUtlProps
- OnPropertyChanged
- CUtlProps.OnPropertyChanged
- CUtlProps::OnPropertyChanged
- SetPropValue
- ATL::CUtlProps<T>::SetPropValue
- ATL.CUtlProps<T>.SetPropValue
- ATL.CUtlProps.SetPropValue
- CUtlProps::SetPropValue
- CUtlProps<T>::SetPropValue
- CUtlProps.SetPropValue
- CUtlProps<T>.SetPropValue
- ATL::CUtlProps::SetPropValue
dev_langs:
- C++
helpviewer_keywords:
- CUtlProps class
- GetPropValue method
- IsValidValue method
- OnInterfaceRequested method
- OnPropertyChanged method
- SetPropValue method
ms.assetid: bb525178-765c-4e23-a110-c0fd70c05437
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0179bbc68bb6ed60f6fadf26f98be492c2eeb4c1
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42571900"
---
# <a name="cutlprops-class"></a>CUtlProps (Clase)
Implementa las propiedades para una variedad de interfaces de la propiedad de OLE DB (por ejemplo, `IDBProperties`, `IDBProperties`, y `IRowsetInfo`).  
  
## <a name="syntax"></a>Sintaxis

```cpp
template < class T >  
class ATL_NO_VTABLE CUtlProps : public CUtlPropsBase  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase que contiene el `BEGIN_PROPSET_MAP`.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  

## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[GetPropValue](#getpropvalue)|Obtiene una propiedad de un conjunto de propiedades.|  
|[IsValidValue](#isvalidvalue)|Se utiliza para validar un valor antes de establecer una propiedad.|  
|[OnInterfaceRequested](#oninterfacerequested)|Controla las solicitudes para una interfaz opcional cuando el consumidor llama a un método de la interfaz de creación de un objeto.|  
|[OnPropertyChanged](#onpropertychanged)|Se llama después de establecer una propiedad para controlar las propiedades encadenadas.|  
|[SetPropValue](#setpropvalue)|Establece una propiedad en un conjunto de propiedades.|  
  
## <a name="remarks"></a>Comentarios  
 La mayor parte de esta clase es un detalle de implementación.  
  
 `CUtlProps` contiene dos miembros para establecer propiedades internamente: [GetPropValue](../../data/oledb/cutlprops-getpropvalue.md) y [SetPropValue](../../data/oledb/cutlprops-setpropvalue.md).  
  
 Para obtener más información sobre las macros utilizadas en una asignación de conjunto de propiedades, vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md) y [END_PROPSET_MAP](../../data/oledb/end-propset-map.md).  
  
## <a name="getpropvalue"></a> CUtlProps:: GetPropValue
Obtiene una propiedad de un conjunto de propiedades.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
OUT_OF_LINE HRESULT GetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pguidPropSet*  
 [in] El GUID para el conjunto de propiedades.  
  
 *dwPropId*  
 [in] El índice de la propiedad.  
  
 *pvValue*  
 [out] Un puntero a una variante que contiene el nuevo valor de propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 `Failure` en el error y S_OK si se realiza correctamente.

## <a name="isvalidvalue"></a> CUtlProps:: IsValidValue
Se utiliza para validar un valor antes de establecer una propiedad.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
virtual HRESULT CUtlPropsBase::IsValidValue(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *iCurSet*  
 El índice de la matriz de conjunto de propiedades; cero si no hay sólo una propiedad establecida.  
  
 *pDBProp*  
 El identificador de propiedad y el nuevo valor en un [DBPROP](/previous-versions/windows/desktop/ms717970\(v=vs.85\)) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar. El valor predeterminado es S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Si dispone de las rutinas de validación que desea ejecutar en un valor que va a utilizar para establecer una propiedad, se debe reemplazar esta función. Por ejemplo, podría validar DBPROP_AUTH_PASSWORD una tabla de la contraseña para determinar un valor válido. 

## <a name="oninterfacerequested"></a> CUtlProps:: Oninterfacerequested
Controla las solicitudes para una interfaz opcional cuando el consumidor llama a un método en uno de los objetos interfaces de creación.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
virtual HRESULT CUtlPropsBase::OnInterfaceRequested(REFIID riid);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *riid*  
 [in] El IID de la interfaz solicitada. Para obtener más información, vea la descripción de la *riid* parámetro de `ICommand::Execute` en el *referencia del programador de OLE DB* (en el *SDK de MDAC*).  
  
### <a name="remarks"></a>Comentarios  
 `OnInterfaceRequested` controla las solicitudes de consumidor de una interfaz opcional cuando el consumidor llama a un método en uno de los objetos interfaces de creación (como `IDBCreateSession`, `IDBCreateCommand`, `IOpenRowset`, o `ICommand`). Establece la propiedad de OLE DB correspondiente de la interfaz solicitada. Por ejemplo, si el consumidor solicita `IID_IRowsetLocate`, `OnInterfaceRequested` establece el `DBPROP_IRowsetLocate` interfaz. Si lo hace, mantiene el estado correcto durante la creación del conjunto de filas.  
  
 Este método se llama cuando el consumidor llama a `IOpenRowset::OpenRowset` o `ICommand::Execute`.  
  
 Si un consumidor abre un objeto y solicita una interfaz opcional, el proveedor debe establecer la propiedad asociada con esa interfaz en VARIANT_TRUE. Para permitir el procesamiento específico de la propiedad, `OnInterfaceRequested` se llama antes de que el proveedor `Execute` se llama al método. De forma predeterminada, `OnInterfaceRequested` controla las interfaces siguientes:  
  
-   `IRowsetLocate`  
  
-   `IRowsetChange`  
  
-   `IRowsetUpdate`  
  
-   `IConnectionPointContainer`  
  
-   `IRowsetScroll`  
  
 Si desea controlar otras interfaces, reemplace esta función en la clase de origen, sesión, comando o conjunto de filas de datos para las funciones del proceso. La invalidación debe avanzar por las interfaces de propiedades normal de get/set para asegurarse de que establecer las propiedades también establece las propiedades encadenadas (consulte [OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md)).  

## <a name="onpropertychanged"></a> CUtlProps:: OnPropertyChanged
Se llama después de establecer una propiedad para controlar las propiedades encadenadas.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
virtual HRESULT OnPropertyChanged(ULONG /* iCurSet */,  
   DBPROP* pDBProp);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *iCurSet*  
 El índice de la matriz de conjunto de propiedades; cero si no hay sólo una propiedad establecida.  
  
 *pDBProp*  
 El identificador de propiedad y el nuevo valor en un [DBPROP](/previous-versions/windows/desktop/ms717970\(v=vs.85\)) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Un HRESULT estándar. El valor predeterminado es S_OK.  
  
### <a name="remarks"></a>Comentarios  
 Si desea controlar las propiedades encadenadas, como marcadores o actualizaciones cuyos valores dependen del valor de otra propiedad, se debe reemplazar esta función.  
  
### <a name="example"></a>Ejemplo  
 En esta función, el usuario obtiene el identificador de propiedad de la `DBPROP*` parámetro. Ahora, es posible comparar el identificador con una propiedad de cadena. Cuando se encuentra la propiedad, `SetProperties` se llama con la propiedad que se establecerá ahora junto con la otra propiedad. En este caso, si uno obtiene el `DBPROP_IRowsetLocate`, `DBPROP_LITERALBOOKMARKS`, o `DBPROP_ORDEREDBOOKMARKS` propiedad, puede establecer el `DBPROP_BOOKMARKS` propiedad.  
  
 [!code-cpp[NVC_OLEDB_Provider#2](../../data/oledb/codesnippet/cpp/cutlprops-onpropertychanged_1.h)]  
  
## <a name="setpropvalue"></a> CUtlProps:: Setpropvalue
Establece una propiedad en un conjunto de propiedades.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT SetPropValue(const GUID* pguidPropSet,  
   DBPROPID dwPropId,  
   VARIANT* pvValue);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *pguidPropSet*  
 [in] El GUID para el conjunto de propiedades.  
  
 *dwPropId*  
 [in] El índice de la propiedad.  
  
 *pvValue*  
 [in] Un puntero a una variante que contiene el nuevo valor de propiedad.  
  
### <a name="return-value"></a>Valor devuelto  
 `Failure` en el error y S_OK si se realiza correctamente. 

## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)