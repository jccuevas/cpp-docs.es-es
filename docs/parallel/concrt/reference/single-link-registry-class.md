---
title: single_link_registry (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- single_link_registry
- AGENTS/concurrency::single_link_registry
- AGENTS/concurrency::single_link_registry::single_link_registry
- AGENTS/concurrency::single_link_registry::add
- AGENTS/concurrency::single_link_registry::begin
- AGENTS/concurrency::single_link_registry::contains
- AGENTS/concurrency::single_link_registry::count
- AGENTS/concurrency::single_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- single_link_registry class
ms.assetid: 09540a4e-c34e-4ff9-af49-21b8612b6ab3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60820d2dc6b4fe0ab5c27ad746ee3f922fc39780
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46045788"
---
# <a name="singlelinkregistry-class"></a>single_link_registry (Clase)
El objeto `single_link_registry` es un `network_link_registry` que administra un solo bloque de origen o bloque de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _Block>
class single_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parámetros  
*Al _bloque al introducir*<br/>
Tipo de los datos del bloque que se almacenan en la `single_link_registry` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[single_link_registry](#ctor)|Construye un objeto `single_link_registry`.|  
|[~ single_link_registry (destructor)](#dtor)|Destruye el objeto `single_link_registry`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[add](#add)|Agrega un vínculo a la `single_link_registry` objeto. (Invalida [network_link_registry:: Add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Devuelve un iterador al primer elemento en el `single_link_registry` objeto. (Invalida [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|  
|[Contiene](#contains)|Busca el `single_link_registry` objeto para un bloque especificado. (Invalida [network_link_registry:: contains](network-link-registry-class.md#contains).)|  
|[count](#count)|Cuenta el número de elementos de la `single_link_registry` objeto. (Invalida [network_link_registry:: Count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Quita un vínculo desde el `single_link_registry` objeto. (Invalida [network_link_registry:: Remove](network-link-registry-class.md#remove).)|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [network_link_registry](network-link-registry-class.md)  
  
 `single_link_registry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add"></a> Agregar 

 Agrega un vínculo a la `single_link_registry` objeto.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_link_target](invalid-link-target-class.md) excepción si ya hay un vínculo en este registro.  
  
##  <a name="begin"></a> comenzar 

 Devuelve un iterador al primer elemento en el `single_link_registry` objeto.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento en el `single_link_registry` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El estado final se indica mediante un `NULL` vínculo.  
  
##  <a name="contains"></a> Contiene 

 Busca el `single_link_registry` objeto para un bloque especificado.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se van a buscar en el `single_link_registry` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si no se encuentra el vínculo, `false` en caso contrario.  
  
##  <a name="count"></a> recuento 

 Cuenta el número de elementos de la `single_link_registry` objeto.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos en el `single_link_registry` objeto.  
  
##  <a name="remove"></a> Quitar 

 Quita un vínculo desde el `single_link_registry` objeto.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el vínculo ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="ctor"></a> single_link_registry) 

 Construye un objeto `single_link_registry`.  
  
```
single_link_registry();
```  
  
##  <a name="dtor"></a> ~ single_link_registry 

 Destruye el objeto `single_link_registry`.  
  
```
virtual ~single_link_registry();
```  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_operation](invalid-operation-class.md) excepción si se llama antes de quita el vínculo.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [multi_link_registry (clase)](multi-link-registry-class.md)
