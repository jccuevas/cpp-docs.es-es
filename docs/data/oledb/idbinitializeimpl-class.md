---
title: IDBInitializeImpl (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.IDBInitializeImpl<T>
- ATL::IDBInitializeImpl<T>
- IDBInitializeImpl
- ATL::IDBInitializeImpl
- ATL.IDBInitializeImpl
- IDBInitializeImpl.IDBInitializeImpl
- IDBInitializeImpl
- IDBInitializeImpl::IDBInitializeImpl
- Initialize
- IDBInitializeImpl::Initialize
- IDBInitializeImpl.Initialize
- IDBInitializeImpl.Uninitialize
- Uninitialize
- IDBInitializeImpl::Uninitialize
- ATL::IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl.m_dwStatus
- ATL.IDBInitializeImpl.m_dwStatus
- IDBInitializeImpl::m_dwStatus
- IDBInitializeImpl<T>::m_dwStatus
- ATL.IDBInitializeImpl<T>.m_dwStatus
- ATL::IDBInitializeImpl<T>::m_dwStatus
- m_dwStatus
- ATL::IDBInitializeImpl<T>::m_pCUtlPropInfo
- m_pCUtlPropInfo
- IDBInitializeImpl::m_pCUtlPropInfo
- ATL.IDBInitializeImpl.m_pCUtlPropInfo
- IDBInitializeImpl<T>::m_pCUtlPropInfo
- IDBInitializeImpl.m_pCUtlPropInfo
- ATL::IDBInitializeImpl::m_pCUtlPropInfo
dev_langs:
- C++
helpviewer_keywords:
- IDBInitializeImpl class
- IDBInitializeImpl constructor
- Initialize method
- Uninitialize method
- m_dwStatus
- m_pCUtlPropInfo
ms.assetid: e4182f81-0443-44f5-a0d3-e7e075d6f883
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 69c7f92110312d4ae8cff427d1081853290919e9
ms.sourcegitcommit: b0d6777cf4b580d093eaf6104d80a888706e7578
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/26/2018
ms.locfileid: "39269929"
---
# <a name="idbinitializeimpl-class"></a>IDBInitializeImpl (Clase)
Proporciona una implementación para el [IDBInitialize](https://msdn.microsoft.com/library/ms713706.aspx) interfaz.  
  
## <a name="syntax"></a>Sintaxis

```cpp
template <class T>  
class ATL_NO_VTABLE IDBInitializeImpl : public IDBInitialize  
```  
  
### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `IDBInitializeImpl`.  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  
  
## <a name="members"></a>Miembros  
  
### <a name="methods"></a>Métodos  
  
|||  
|-|-|  
|[IDBInitializeImpl](#idbinitializeimpl)|El constructor.|  
  
### <a name="interface-methods"></a>Métodos de interfaz  
  
|||  
|-|-|  
|[Initialize](#initialize)|Inicia el proveedor.|  
|[Anular la inicialización](#uninitialize)|Detiene el proveedor.|  
  
### <a name="data-members"></a>Miembros de datos  
  
|||  
|-|-|  
|[m_dwStatus](#dwstatus)|Indicadores del origen de datos.|  
|[m_pCUtlPropInfo](#pcutlpropinfo)|Un puntero a la implementación de la información de las propiedades de la base de datos.|  
  
## <a name="remarks"></a>Comentarios  
 Una interfaz obligatoria en los objetos de origen de datos y una interfaz opcional sobre los enumeradores.  

## <a name="idbinitializeimpl"></a> Idbinitializeimpl:: Idbinitializeimpl
El constructor.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
IDBInitializeImpl();  
  
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa a todos los miembros de datos. 
  
## <a name="initialize"></a> Idbinitializeimpl:: Initialize
Inicializa el objeto de origen de datos mediante la preparación de su compatibilidad con la propiedad.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(Initialize)(void);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDBInitialize:: Initialize](https://msdn.microsoft.com/library/ms718026.aspx) en el *referencia del programador OLE DB*. 

## <a name="uninitialize"></a> Idbinitializeimpl:: UnInitialize
Coloca los datos del origen de objeto en un estado no inicializado al liberar los recursos internos, como la compatibilidad con la propiedad.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
      STDMETHOD(Uninitialize)(void);  
```  
  
### <a name="remarks"></a>Comentarios  
 Consulte [IDBInitialize:: UnInitialize](https://msdn.microsoft.com/library/ms719648.aspx) en el *referencia del programador OLE DB*.

## <a name="dwstatus"></a> Idbinitializeimpl:: M_dwstatus
Indicadores del origen de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
DWORD m_dwStatus;  
  
```  
  
### <a name="remarks"></a>Comentarios  
 Estas marcas especifican o indican el estado de varios atributos para el objeto de origen de datos. Contiene uno o varios de los siguientes **enum** valores:  
  
```  
enum DATASOURCE_FLAGS {  
    DSF_MASK_INIT     = 0xFFFFF00F,  
    DSF_PERSIST_DIRTY = 0x00000001,  
    DSF_INITIALIZED   = 0x00000010,  
};  
```  
  
|||  
|-|-|  
|`DSF_MASK_INIT`|Una máscara para habilitar la restauración de estado no inicializado.|  
|`DSF_PERSIST_DIRTY`|Establece si el objeto de origen de datos requiere la persistencia (es decir, si ha habido cambios).|  
|`DSF_INITIALIZED`|Establecer si se ha inicializado el origen de datos.|  

## <a name="pcutlpropinfo"></a> Idbinitializeimpl:: M_pcutlpropinfo
Un puntero al objeto de implementación para la información de las propiedades de la base de datos.  
  
### <a name="syntax"></a>Sintaxis  
  
```cpp
CUtlPropInfo<  
T  
>* m_pCUtlPropInfo;  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)
