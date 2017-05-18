---
title: Clase CComSingleThreadModel | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 050e7483670bd32f633660ba44491c8bb3fc462d
ms.openlocfilehash: ff5d8d2ced1d6fe0196888d8c746844ace8307f8
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomsinglethreadmodel-class"></a>Clase CComSingleThreadModel
Esta clase proporciona métodos para aumentar y disminuir el valor de una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Hace referencia a clase `CComFakeCriticalSection`.|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Referencias `CComSingleThreadModel`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|Disminuye el valor de la variable especificada. Esta implementación no es segura para subprocesos.|  
|[CComSingleThreadModel::Increment](#increment)|Incrementa el valor de la variable especificada. Esta implementación no es segura para subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 `CComSingleThreadModel`Proporciona métodos para aumentar y disminuir el valor de una variable. A diferencia de [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), estos métodos no son seguros para subprocesos.  

 Normalmente, se utiliza `CComSingleThreadModel` a través de uno de dos `typedef` nombres, ya sea [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) o [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). La clase hace referencia a cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  

  
|definición de tipos|Modelo de subprocesamiento sencillo|Modelo de subprocesamiento controlado|Modelo de subprocesamiento libre|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 `CComSingleThreadModel`Sí define tres `typedef` nombres. `ThreadModelNoCS`referencias `CComSingleThreadModel`. `AutoCriticalSection`y `CriticalSection` hacen referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados a obtener y liberar la propiedad de una sección crítica.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection  
 Al usar `CComSingleThreadModel`, `typedef` nombre `AutoCriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Porque `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones de `AutoCriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `AutoCriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Además `AutoCriticalSection`, puede utilizar el `typedef` nombre [CriticalSection](#criticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>CComSingleThreadModel::CriticalSection  
 Al usar `CComSingleThreadModel`, `typedef` nombre `CriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Porque `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones de `CriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `CriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Además `CriticalSection`, puede utilizar el `typedef` nombre [AutoCriticalSection](#autocriticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>CComSingleThreadModel::Decrement  
 Este disminuye función estática el valor de la variable apunta a `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a reducir.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado de la reducción.  
  
##  <a name="increment"></a>CComSingleThreadModel::Increment  
 Este disminuye función estática el valor de la variable apunta a `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a incrementar.  
  
### <a name="return-value"></a>Valor devuelto  
 El resultado del incremento.  
  
##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS  
 Al usar `CComSingleThreadModel`, `typedef` nombre `ThreadModelNoCS` simplemente hace referencia a `CComSingleThreadModel`.  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Comentarios  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) contienen definiciones de `ThreadModelNoCS`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase que se hace referencia a `ThreadModelNoCS`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

