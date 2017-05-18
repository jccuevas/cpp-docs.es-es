---
title: multi_link_registry (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: b52ee20ed16a4ce8d0b9f11b6acf25112464b49b
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[multi_link_registry](#ctor)|Construye un objeto `multi_link_registry`.|  
|[~ multi_link_registry (destructor)](#dtor)|Destruye el objeto `multi_link_registry`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[add](#add)|Agrega un vínculo a la `multi_link_registry` objeto. (Invalida [network_link_registry:: Add](network-link-registry-class.md#add).)|  
|[begin](#begin)|Devuelve un iterador al primer elemento de la `multi_link_registry` objeto. (Invalida [network_link_registry:: BEGIN](network-link-registry-class.md#begin).)|  
|[contiene](#contains)|Busca la `multi_link_registry` objeto para un bloque especificado. (Invalida [network_link_registry:: contains](network-link-registry-class.md#contains).)|  
|[count](#count)|Cuenta el número de elementos de la `multi_link_registry` objeto. (Invalida [network_link_registry:: Count](network-link-registry-class.md#count).)|  
|[remove](#remove)|Quita un vínculo desde el `multi_link_registry` objeto. (Invalida [network_link_registry:: Remove](network-link-registry-class.md#remove).)|  
|[set_bound](#set_bound)|Establece un límite superior en el número de vínculos que el `multi_link_registry` puede contener el objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [network_link_registry](network-link-registry-class.md)  
  
 `multi_link_registry`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add"></a>Agregar 

 Agrega un vínculo a la `multi_link_registry` objeto.  
  
```
virtual void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Puntero a un bloque que se va a agregar.  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_link_target](invalid-link-target-class.md) excepción si el vínculo ya está presente en el registro, o si un límite ya se estableció con la `set_bound` (función) y un vínculo que se ha quitado.  
  
##  <a name="begin"></a>comenzar 

 Devuelve un iterador al primer elemento de la `multi_link_registry` objeto.  
  
```
virtual iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento de la `multi_link_registry` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El estado final se indica mediante un `NULL` vínculo.  
  
##  <a name="contains"></a>contiene 

 Busca la `multi_link_registry` objeto para un bloque especificado.  
  
```
virtual bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a buscar en la `multi_link_registry` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si no se encuentra el bloque especificado, `false` en caso contrario.  
  
##  <a name="count"></a>recuento 

 Cuenta el número de elementos de la `multi_link_registry` objeto.  
  
```
virtual size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de elementos de la `multi_link_registry` objeto.  
  
##  <a name="ctor"></a>multi_link_registry 

 Construye un objeto `multi_link_registry`.  
  
```
multi_link_registry();
```  
  
##  <a name="dtor"></a>~ multi_link_registry 

 Destruye el objeto `multi_link_registry`.  
  
```
virtual ~multi_link_registry();
```  
  
### <a name="remarks"></a>Comentarios  
 El método produce una [invalid_operation](invalid-operation-class.md) excepción si se llama antes de quitarán todos los vínculos.  
  
##  <a name="remove"></a>quitar 

 Quita un vínculo desde el `multi_link_registry` objeto.  
  
```
virtual bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vínculo ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="set_bound"></a>set_bound 

 Establece un límite superior en el número de vínculos que el `multi_link_registry` puede contener el objeto.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MaxLinks`  
 El número máximo de vínculos que el `multi_link_registry` puede contener el objeto.  
  
### <a name="remarks"></a>Comentarios  
 Después de establece un límite, desvincular una entrada hará que el `multi_link_registry` objeto que se va a entrar en un estado inmutable donde más llamadas a `add` producirá un `invalid_link_target` excepción.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [single_link_registry (clase)](single-link-registry-class.md)

