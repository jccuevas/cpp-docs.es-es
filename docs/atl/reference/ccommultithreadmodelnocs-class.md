---
title: Clase CComMultiThreadModelNoCS | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CComMultiThreadModelNoCS
- CComMultiThreadModelNoCS
- ATL.CComMultiThreadModelNoCS
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: 1a00023e4d3e31ddb6381e90a50231449b1de18d
ms.openlocfilehash: dd14e5c941da5383dce19e9f7f539bfb9909759f
ms.lasthandoff: 02/28/2017

---
# <a name="ccommultithreadmodelnocs-class"></a>Clase CComMultiThreadModelNoCS
`CComMultiThreadModelNoCS`Proporciona métodos de subprocesos para aumentar y disminuir el valor de una variable, sin bloqueo de sección crítica o la funcionalidad desbloquea.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Hace referencia a clase `CComFakeCriticalSection`.|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Hace referencia a clase `CComMultiThreadModelNoCS`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|  
|[CComMultiThreadModelNoCS::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 `CComMultiThreadModelNoCS`es similar a [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) en que proporciona los métodos de subprocesos para aumentar y disminuir una variable. Sin embargo, al hacer referencia a una clase de sección crítica a través de `CComMultiThreadModelNoCS`, métodos como `Lock` y `Unlock` no hará nada.  
  
 Normalmente, se utiliza `CComMultiThreadModelNoCS` a través de la `ThreadModelNoCS` `typedef` nombre. Esto `typedef` se define en `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).  
  
> [!NOTE]
>  Global `typedef` nombres [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) y [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) no hacen referencia a `CComMultiThreadModelNoCS`.  
  
 Además `ThreadModelNoCS`, `CComMultiThreadModelNoCS` define `AutoCriticalSection` y `CriticalSection`. Estas dos últimas `typedef` nombres hagan referencia a [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), que proporciona métodos vacíos asociados a obtener y liberar una sección crítica.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-nameautocriticalsectiona--ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection  
 Al usar `CComMultiThreadModelNoCS`, `typedef` nombre `AutoCriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Porque `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contiene las definiciones de `AutoCriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `AutoCriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Además `AutoCriticalSection`, puede utilizar el `typedef` nombre [CriticalSection](#criticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="a-namecriticalsectiona--ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection  
 Al usar `CComMultiThreadModelNoCS`, `typedef` nombre `CriticalSection` hace referencia a clase [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 Porque `CComFakeCriticalSection` no proporciona una sección crítica, sus métodos no hacen nada.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contiene las definiciones de `CriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `CriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Además `CriticalSection`, puede utilizar el `typedef` nombre `AutoCriticalSection`. No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="a-namedecrementa--ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement  
 Esta función estática llama a la función de Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), que disminuye el valor de la variable apunta a `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a reducir.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado de la reducción es 0, a continuación, `Decrement` devuelve 0. Si el resultado de la reducción es distinto de cero, el valor devuelto también es distinto de cero, pero no puede igualar el resultado de la reducción.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedDecrement** impide que varios subprocesos simultáneamente usando esta variable.  
  
##  <a name="a-nameincrementa--ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Increment  
 Esta función estática llama a la función de Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), lo que aumenta el valor de la variable apuntado a `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a incrementar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado del incremento es 0, a continuación, **incremento** devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero no puede igualar el resultado del incremento.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedIncrement** impide que varios subprocesos simultáneamente usando esta variable.  
  
##  <a name="a-namethreadmodelnocsa--ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS  
 Al usar `CComMultiThreadModelNoCS`, `typedef` nombre `ThreadModelNoCS` simplemente hace referencia a `CComMultiThreadModelNoCS`.  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Comentarios  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) y [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) también contiene las definiciones de `ThreadModelNoCS`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase que se hace referencia a `ThreadModelNoCS`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 Tenga en cuenta que la definición de `ThreadModelNoCS` en `CComMultiThreadModelNoCS` proporciona simetría con `CComMultiThreadModel` y `CComSingleThreadModel`. Por ejemplo, suponga que el código de ejemplo en `CComMultiThreadModel::AutoCriticalSection` declara los siguientes `typedef`:  
  
 [!code-cpp[NVC_ATL_COM&#37;](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 Independientemente de la clase especificada para `ThreadModel` (como `CComMultiThreadModelNoCS`), `_ThreadModel` se resuelve como corresponda.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)
