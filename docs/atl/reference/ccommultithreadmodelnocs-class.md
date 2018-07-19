---
title: CComMultiThreadModelNoCS (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 65f8021bdc16dcfb2c4d1aa69936f27cfe7ac1df
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884823"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS (clase)
`CComMultiThreadModelNoCS` Proporciona métodos seguros para subprocesos para aumentar y disminuir el valor de una variable, sin bloqueo de sección crítica o funcionalidad de desbloqueo.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Hace referencia a clase `CComFakeCriticalSection`.|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Hace referencia a clase `CComMultiThreadModelNoCS`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|  
|[CComMultiThreadModelNoCS::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 `CComMultiThreadModelNoCS` es similar a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en que proporciona métodos seguros para subprocesos para aumentar y disminuir una variable. Sin embargo, al hacer referencia a una clase de sección crítica a través de `CComMultiThreadModelNoCS`, métodos, como `Lock` y `Unlock` no hará nada.  
  
 Normalmente, se utiliza `CComMultiThreadModelNoCS` a través de la `ThreadModelNoCS` **typedef** nombre. Esto **typedef** se define en `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).  
  
> [!NOTE]
>  Global **typedef** nombres [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) y [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) no hacen referencia a `CComMultiThreadModelNoCS`.  
  
 Además `ThreadModelNoCS`, `CComMultiThreadModelNoCS` define `AutoCriticalSection` y `CriticalSection`. Estos dos últimos **typedef** los nombres de referencia [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados con la obtención y liberación de una sección crítica.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection  
 Cuando se usa `CComMultiThreadModelNoCS`, **typedef** nombre `AutoCriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Dado que `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen las definiciones para `AutoCriticalSection`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica al que hace referencia `AutoCriticalSection`:  
  
|Clase definida en|Clase que se hace referenciada|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Además `AutoCriticalSection`, puede usar el **typedef** nombre [CriticalSection](#criticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection  
 Cuando se usa `CComMultiThreadModelNoCS`, **typedef** nombre `CriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Dado que `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen las definiciones para `CriticalSection`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica al que hace referencia `CriticalSection`:  
  
|Clase definida en|Clase que se hace referenciada|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Además `CriticalSection`, puede usar el **typedef** nombre `AutoCriticalSection`. No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement  
 Esta función estática llama a la función de Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), que disminuye el valor de la variable apunta a *p*.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 [in] Puntero a la variable que se va a reducir.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado de la reducción es 0, a continuación, `Decrement` devuelve 0. Si el resultado de la reducción es distinto de cero, el valor devuelto también es distinto de cero, pero no puede ser igual al resultado de la reducción.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedDecrement** impide que más de un subproceso de forma simultánea con esta variable.  
  
##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment  
 Esta función estática llama a la función de Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), lo que incrementa el valor de la variable apuntado *p*.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 [in] Puntero a la variable que se va a incrementar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado del incremento es 0, a continuación, **incremento** devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero no puede ser igual al resultado del incremento.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedIncrement** impide que más de un subproceso de forma simultánea con esta variable.  
  
##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS  
 Cuando se usa `CComMultiThreadModelNoCS`, **typedef** nombre `ThreadModelNoCS` simplemente hace referencia a `CComMultiThreadModelNoCS`.  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Comentarios  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contienen las definiciones para `ThreadModelNoCS`. En la tabla siguiente se muestra la relación entre la clase del modelo de subprocesos y la clase al que hace referencia `ThreadModelNoCS`:  
  
|Clase definida en|Clase que se hace referenciada|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 Tenga en cuenta que la definición de `ThreadModelNoCS` en `CComMultiThreadModelNoCS` ofrece simetría con `CComMultiThreadModel` y `CComSingleThreadModel`. Por ejemplo, suponga que el código de ejemplo en `CComMultiThreadModel::AutoCriticalSection` declara lo siguiente **typedef**:  
  
 [!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 Independientemente de la clase especificada para `ThreadModel` (como `CComMultiThreadModelNoCS`), `_ThreadModel` se resuelve en consecuencia.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)