---
title: single_link_registry (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- agents/concurrency::single_link_registry
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 3f4719881fac882611f68b36d410c0611f99ba01
ms.lasthandoff: 02/24/2017

---
# <a name="singlelinkregistry-class"></a>single_link_registry (Clase)
El objeto `single_link_registry` es un `network_link_registry` que administra un solo bloque de origen o bloque de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Block`  
 Tipo de los datos del bloque que se almacenan en la `single_link_registry` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[single_link_registry (Constructor)](#ctor)|Construye un objeto `single_link_registry`.|  
|[~ single_link_registry (destructor)](#dtor)|Destruye el objeto `single_link_registry`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[el método Add](#add)|Agrega un vínculo a la `single_link_registry` objeto. (Invalida [network_link_registry:: Add](network-link-registry-class.md#add).)|  
|[Begin (método)](#begin)|Devuelve un iterador al primer elemento de la `single_link_registry` objeto. (Invalida [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|  
|[Contains (método)](#contains)|Busca la `single_link_registry` objeto para un bloque especificado. (Invalida [network_link_registry:: contains](network-link-registry-class.md#contains).)|  
|[Count (método)](#count)|Cuenta el número de elementos de la `single_link_registry` objeto. (Invalida [network_link_registry:: Count](network-link-registry-class.md#count).)|  
|[Remove (método)](#remove)|Quita un vínculo desde el `single_link_registry` objeto. (Invalida [network_link_registry:: Remove](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-nameadda-add"></a><a name="add"></a>Agregar 

 Agrega un vínculo a la `single_link_registry` objeto.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Puntero a un bloque que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_link_target](invalid-link-target-class.md) excepción si ya hay un vínculo en este registro.  
  
##  <a name="a-namebegina-begin"></a><a name="begin"></a>comenzar 

 Devuelve un iterador al primer elemento de la `single_link_registry` objeto.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento de la `single_link_registry` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El estado final se indica mediante un `NULL` vínculo.  
  
##  <a name="a-namecontainsa-contains"></a><a name="contains"></a>contiene 

 Busca la `single_link_registry` objeto para un bloque especificado.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a buscar en la `single_link_registry` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si no se encuentra el vínculo, `false` en caso contrario.  
  
##  <a name="a-namecounta-count"></a><a name="count"></a>recuento 

 Cuenta el número de elementos de la `single_link_registry` objeto.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la `single_link_registry` objeto.  
  
##  <a name="a-nameremovea-remove"></a><a name="remove"></a>quitar 

 Quita un vínculo desde el `single_link_registry` objeto.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vínculo ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="a-namectora-singlelinkregistry"></a><a name="ctor"></a>single_link_registry 

 Construye un objeto `single_link_registry`.  
  
```
single_link_registry();
```  
  
##  <a name="a-namedtora-singlelinkregistry"></a><a name="dtor"></a>~ single_link_registry 

 Destruye el objeto `single_link_registry`.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_operation](invalid-operation-class.md) excepción si se llama antes de quita el vínculo.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [multi_link_registry (clase)](multi-link-registry-class.md)

