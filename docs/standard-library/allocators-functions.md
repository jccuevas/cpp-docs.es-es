---
title: '&lt;allocators&gt; (macros) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/std::ALLOCATOR_DECL
- allocators/std::CACHE_CHUNKLIST
- allocators/std::CACHE_FREELIST
- allocators/std::CACHE_SUBALLOC
- allocators/std::SYNC_DEFAULT
ms.assetid: 9cb5ee07-1ff9-4594-ae32-3c8c6efb511a
caps.latest.revision: 12
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: da17f9af1f14df13eb3871ef9ccf785356e02de4
ms.openlocfilehash: abc1dd29ba68540a6669f7aff1bbd3dffdab616a
ms.lasthandoff: 02/24/2017

---
# <a name="ltallocatorsgt-macros"></a>&lt;allocators&gt; (macros)
||||  
|-|-|-|  
|[ALLOCATOR_DECL](#allocator_decl)|[CACHE_CHUNKLIST](#cache_chunklist)|[CACHE_FREELIST](#cache_freelist)|  
|[CACHE_SUBALLOC](#cache_suballoc)|[SYNC_DEFAULT](#sync_default)|  
  
##  <a name="allocator_decl"></a>  ALLOCATOR_DECL  
 Da como resultado una clase de plantilla de asignador.  
  
```
#define ALLOCATOR_DECL(cache, sync, name) <alloc_template>
```  
  
### <a name="remarks"></a>Comentarios  
 La macro produce una definición de plantilla `template <class Type> class name {.....}` y una especialización `template <> class name<void> {.....}` que definen una clase de plantilla de asignador que usa el filtro de sincronización `sync` y una memoria caché de tipo `cache`.  
  
 En el caso de los compiladores que pueden compilar reenlaces, la definición de plantilla resultante tiene el siguiente aspecto:  
```  
struct rebind
   {    /* convert a name<Type> to a name<Other> */
   typedef name<Other> other;
   };  
 ```  
 En el caso de los compiladores que no pueden compilar reenlaces, la definición de plantilla resultante tiene el siguiente aspecto:  
  
```
template <class Type<class name
    : public stdext::allocators::allocator_base<Type,
    sync<stdext::allocators::rts_alloc<cache>>>
{
public:
    name() {}
    template <class Other>
    name(const name<Other>&) {}
    template <class Other>
    name& operator= (const name<Other>&)
    {
        return *this;
    }
};
```  
  
##  <a name="cache_chunklist"></a>  CACHE_CHUNKLIST  
 Produce `stdext::allocators::cache_chunklist<sizeof(Type)>`.  
  
```
#define CACHE_CHUNKLIST <cache_class>
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cache_freelist"></a>  CACHE_FREELIST  
 Produce `stdext::allocators::cache_freelist<sizeof(Type), max>`.  
  
```
#define CACHE_FREELIST(max) <cache_class>
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="cache_suballoc"></a>  CACHE_SUBALLOC  
 Produce `stdext::allocators::cache_suballoc<sizeof(Type)>`.  
  
```
#define CACHE_SUBALLOC <cache_class>
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="sync_default"></a>  SYNC_DEFAULT  
 Da como resultado un filtro de sincronización.  
  
```
#define SYNC_DEFAULT <sync_template>
```  
  
### <a name="remarks"></a>Comentarios  
 Si un compilador admite la compilación de aplicaciones de un único subproceso y de varios, en el caso de las aplicaciones de un único subproceso la macro produce `stdext::allocators::sync_none`; en todos los demás casos, produce `stdext::allocators::sync_shared`.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)





