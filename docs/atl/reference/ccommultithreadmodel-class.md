---
title: Clase CComMultiThreadModel | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
caps.latest.revision: 21
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
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6dbfb33a717b23e8252c9bcb2fc11b4a6e420280
ms.lasthandoff: 02/24/2017

---
# <a name="ccommultithreadmodel-class"></a>Clase CComMultiThreadModel
`CComMultiThreadModel`Proporciona métodos de subprocesos para aumentar y disminuir el valor de una variable.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Hace referencia a clase [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Hace referencia a clase [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Hace referencia a clase [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|(Estático) Disminuye el valor de la variable especificada de una manera segura para subprocesos.|  
|[CComMultiThreadModel::Increment](#increment)|(Estático) Incrementa el valor de la variable especificada de una manera segura para subprocesos.|  
  
## <a name="remarks"></a>Comentarios  
 Normalmente, se utiliza `CComMultiThreadModel` a través de uno de dos `typedef` nombres, ya sea [CComObjectThreadModel] (atl-typedefs.md #ccomobjectthreadmodel o [CComGlobalsThreadModel] (atl-typedefs.md #ccomglobalsthreadmodel. La clase hace referencia a cada `typedef` depende del modelo de subprocesos utilizado, como se muestra en la tabla siguiente:  
  
|definición de tipos|Subprocesamiento único|Subproceso de apartamento|Subprocesamiento libre|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S= `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 `CComMultiThreadModel`Sí define tres `typedef` nombres. `AutoCriticalSection`y `CriticalSection` hacen referencia a las clases que proporcionan métodos para obtener y liberar la propiedad de una sección crítica. `ThreadModelNoCS`referencias de clase [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection  
 Al usar `CComMultiThreadModel`, `typedef` nombre `AutoCriticalSection` hace referencia a clase [CComAutoCriticalSection](ccomautocriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contiene las definiciones de `AutoCriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `AutoCriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Además `AutoCriticalSection`, puede utilizar el `typedef` nombre [CriticalSection](#criticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 El siguiente código se modela después de [CComObjectRootEx](ccomobjectrootex-class.md)y se muestra `AutoCriticalSection` se utiliza en un entorno de subprocesos.  
  

```cpp  
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);   
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```  
  
 Las siguientes tablas muestran los resultados de la `InternalAddRef` y `Lock` métodos, dependiendo de la **ThreadModel** parámetro de plantilla y el modelo de subprocesos utilizado por la aplicación:  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|Método|Único o subprocesamiento controlado|Subprocesamiento libre|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|El incremento no es segura para subprocesos.|El incremento es segura para subprocesos.|  
|`Lock`|No hace nada; No hay ninguna sección crítica para bloquear.|La sección crítica está bloqueada.|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|Método|Único o subprocesamiento controlado|Subprocesamiento libre|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|El incremento no es segura para subprocesos.|El incremento es segura para subprocesos.|  
|`Lock`|No hace nada; No hay ninguna sección crítica para bloquear.|No hace nada; No hay ninguna sección crítica para bloquear.|  
  
##  <a name="criticalsection"></a>CComMultiThreadModel::CriticalSection  
 Al usar `CComMultiThreadModel`, `typedef` nombre `CriticalSection` hace referencia a clase [CComCriticalSection](ccomcriticalsection-class.md), que proporciona métodos para obtener y liberar la propiedad de un objeto de sección crítica.  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Comentarios  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) y [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) también contiene las definiciones de `CriticalSection`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase de sección crítica que hace referencia a `CriticalSection`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Además `CriticalSection`, puede utilizar el `typedef` nombre [AutoCriticalSection](#autocriticalsection). No se debe especificar `AutoCriticalSection` en objetos globales o miembros de clase estáticos si desea eliminar el código de inicio de CRT.  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
##  <a name="decrement"></a>CComMultiThreadModel::Decrement  
 Esta función estática llama a la función de Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), que disminuye el valor de la variable apunta a `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a reducir.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado de la reducción es 0, a continuación, `Decrement` devuelve 0. Si el resultado de la reducción es distinto de cero, el valor devuelto también es distinto de cero, pero no puede igualar el resultado de la reducción.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedDecrement** impide que varios subprocesos simultáneamente usando esta variable.  
  
##  <a name="increment"></a>CComMultiThreadModel::Increment  
 Esta función estática llama a la función de Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), lo que aumenta el valor de la variable apuntado a `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 [in] Puntero a la variable que se va a incrementar.  
  
### <a name="return-value"></a>Valor devuelto  
 Si el resultado del incremento es 0, a continuación, **incremento** devuelve 0. Si el resultado del incremento es distinto de cero, el valor devuelto también es distinto de cero, pero no puede igualar el resultado del incremento.  
  
### <a name="remarks"></a>Comentarios  
 **InterlockedIncrement** impide que varios subprocesos simultáneamente usando esta variable.  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS  
 Al usar `CComMultiThreadModel`, `typedef` nombre `ThreadModelNoCS` hace referencia a clase [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Comentarios  
 `CComMultiThreadModelNoCS`Proporciona métodos de subprocesos para aumentar y disminuir una variable; Sin embargo, no proporciona una sección crítica.  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) y `CComMultiThreadModelNoCS` también contiene las definiciones de `ThreadModelNoCS`. En la tabla siguiente muestra la relación entre la clase del modelo de subprocesos y la clase que se hace referencia a `ThreadModelNoCS`:  
  
|Clase definida en|Referenciada de clase|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Ejemplo  
 Consulte [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
## <a name="see-also"></a>Vea también  
 [Clase CComSingleThreadModel](ccomsinglethreadmodel-class.md)   
 [Clase CComAutoCriticalSection](ccomautocriticalsection-class.md)   
 [Clase CComCriticalSection](ccomcriticalsection-class.md)   
 [Información general de la clase](../atl-class-overview.md)

