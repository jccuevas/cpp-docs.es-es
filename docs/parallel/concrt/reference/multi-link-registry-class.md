---
title: multi_link_registry (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- multi_link_registry
- AGENTS/concurrency::multi_link_registry
- AGENTS/concurrency::multi_link_registry::multi_link_registry
- AGENTS/concurrency::multi_link_registry::add
- AGENTS/concurrency::multi_link_registry::begin
- AGENTS/concurrency::multi_link_registry::contains
- AGENTS/concurrency::multi_link_registry::count
- AGENTS/concurrency::multi_link_registry::remove
- AGENTS/concurrency::multi_link_registry::set_bound
dev_langs:
- C++
helpviewer_keywords:
- multi_link_registry class
ms.assetid: b2aa73a8-e8a6-4255-b117-d07530c328b2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8f87da4852fff0256b5ca55cfd47d839531b8a03
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="multilinkregistry-class"></a>multi_link_registry (Clase)
El objeto `multi_link_registry` es un `network_link_registry` que administra varios bloques de origen o varios bloques de destino.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _Block>
class multi_link_registry : public network_link_registry<_Block>;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_Block`  
 Tipo de los datos del bloque que se almacenan en la `multi_link_registry` objeto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|Construye un objeto `multi_link_registry`.|  
|[~multi_link_registry Destructor](#dtor)|Destruye el objeto `multi_link_registry`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[add](#add)|Agrega un vínculo a la `multi_link_registry` objeto. (Overrides [network_link_registry::add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Devuelve un iterador al primer elemento en el `multi_link_registry` objeto. (Overrides [network_link_registry::begin](network-link-registry-class.md#begin).)|  
|[contiene](#contains)|Busca el `multi_link_registry` objeto para un bloque especificado. (Invalida [network_link_registry:: contains](network-link-registry-class.md#contains).)|  
|[count](#count)|Cuenta el número de elementos de la `multi_link_registry` objeto. (Overrides [network_link_registry::count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Quita un vínculo desde el `multi_link_registry` objeto. (Overrides [network_link_registry::remove](network-link-registry-class.md#remove).)|  
|[set_bound](#set_bound)|Establece un límite superior en el número de vínculos que los `multi_link_registry` objeto puede contener.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add"></a> Agregar 

 Agrega un vínculo a la `multi_link_registry` objeto.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_link_target](invalid-link-target-class.md) excepción si el vínculo ya está presente en el registro, o si un límite ya se estableció con la `set_bound` función y un vínculo que se ha quitado.  
  
##  <a name="begin"></a> BEGIN 

 Devuelve un iterador al primer elemento en el `multi_link_registry` objeto.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento en el `multi_link_registry` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El estado final se indica mediante un `NULL` vínculo.  
  
##  <a name="contains"></a> contiene 

 Busca el `multi_link_registry` objeto para un bloque especificado.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a buscar en la `multi_link_registry` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si se encontró el bloque especificado, `false` en caso contrario.  
  
##  <a name="count"></a> Recuento 

 Cuenta el número de elementos de la `multi_link_registry` objeto.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la `multi_link_registry` objeto.  
  
##  <a name="ctor"></a> multi_link_registry 

 Construye un objeto `multi_link_registry`.  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a> ~multi_link_registry 

 Destruye el objeto `multi_link_registry`.  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_operation](invalid-operation-class.md) excepción si se llama antes de que se quitan todos los vínculos.  
  
##  <a name="remove"></a> Quitar 

 Quita un vínculo desde el `multi_link_registry` objeto.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el vínculo se ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="set_bound"></a> set_bound 

 Establece un límite superior en el número de vínculos que los `multi_link_registry` objeto puede contener.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MaxLinks`  
 El número máximo de vínculos que los `multi_link_registry` objeto puede contener.  
  
### <a name="remarks"></a>Comentarios  
 Después de establece un límite, desvincular una entrada hará que el `multi_link_registry` objeto para entrar en un estado inmutable donde realizarán llamadas posteriores a `add` producirá un `invalid_link_target` excepción.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [single_link_registry (clase)](single-link-registry-class.md)
