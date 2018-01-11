---
title: source_link_manager (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- source_link_manager
- AGENTS/concurrency::source_link_manager
- AGENTS/concurrency::source_link_manager::source_link_manager
- AGENTS/concurrency::source_link_manager::add
- AGENTS/concurrency::source_link_manager::begin
- AGENTS/concurrency::source_link_manager::contains
- AGENTS/concurrency::source_link_manager::count
- AGENTS/concurrency::source_link_manager::reference
- AGENTS/concurrency::source_link_manager::register_target_block
- AGENTS/concurrency::source_link_manager::release
- AGENTS/concurrency::source_link_manager::remove
- AGENTS/concurrency::source_link_manager::set_bound
dev_langs: C++
helpviewer_keywords: source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 67cf15c6681c989a2da2b4e6824fec6012c517bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="sourcelinkmanager-class"></a>source_link_manager (Clase)
El objeto `source_link_manager` administra los vínculos de red del bloque de mensajería para los bloques `ISource`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>Parámetros  
 `_LinkRegistry`  
 El registro del vínculo de red.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un `source_link_manager` objeto.|  
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un `source_link_manager` objeto para leer y realizar operaciones const.|  
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento de la `source_link_manager` objeto.|  
|`type`|El tipo de registro de vínculo está administrado por el `source_link_manager` objeto.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source_link_manager)](#ctor)|Construye un objeto `source_link_manager`.|  
|[~ source_link_manager (destructor)](#dtor)|Destruye el objeto `source_link_manager`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[add](#add)|Agrega un vínculo de origen a la `source_link_manager` objeto.|  
|[begin](#begin)|Devuelve un iterador al primer elemento en el `source_link_manager` objeto.|  
|[contiene](#contains)|Busca el `network_link_registry` dentro de este `source_link_manager` objeto para un bloque especificado.|  
|[count](#count)|Cuenta el número de bloques vinculados en el `source_link_manager` objeto.|  
|[reference](#reference)|Adquiere una referencia en la `source_link_manager` objeto.|  
|[register_target_block](#register_target_block)|Registra el bloque de destino que contiene este `source_link_manager` objeto.|  
|[release](#release)|Libera la referencia en la `source_link_manager` objeto.|  
|[remove](#remove)|Quita un vínculo desde el `source_link_manager` objeto.|  
|[set_bound](#set_bound)|Establece el número máximo de vínculos de origen que se pueden agregar a este `source_link_manager` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Actualmente, los bloques de origen son cuentan las referencias. Se trata de un contenedor en un `network_link_registry` objeto que permite el acceso simultáneo a los vínculos y proporciona la capacidad de hacer referencia a los vínculos a través de las devoluciones de llamada. Bloques de mensajes ( `target_block`s o `propagator_block`s) debe usar esta clase para sus vínculos de origen.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `source_link_manager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add"></a>Agregar 

 Agrega un vínculo de origen a la `source_link_manager` objeto.  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a agregar.  
  
##  <a name="begin"></a>comenzar 

 Devuelve un iterador al primer elemento en el `source_link_manager` objeto.  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento en el `source_link_manager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 El estado final del iterador se indica mediante un `NULL` vínculo.  
  
##  <a name="contains"></a>contiene 

 Busca el `network_link_registry` dentro de este `source_link_manager` objeto para un bloque especificado.  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a buscar en la `source_link_manager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si se encontró el bloque especificado, `false` en caso contrario.  
  
##  <a name="count"></a>recuento 

 Cuenta el número de bloques vinculados en el `source_link_manager` objeto.  
  
```
size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bloques vinculados del `source_link_manager` objeto.  
  
##  <a name="reference"></a>referencia 

 Adquiere una referencia en la `source_link_manager` objeto.  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a>register_target_block 

 Registra el bloque de destino que contiene este `source_link_manager` objeto.  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
 `_PTarget`  
 El bloque de destino que contiene este `source_link_manager` objeto.  
  
##  <a name="release"></a>la versión 

 Libera la referencia en la `source_link_manager` objeto.  
  
```
void release();
```  
  
##  <a name="remove"></a>quitar 

 Quita un vínculo desde el `source_link_manager` objeto.  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Link`  
 Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el vínculo se ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="set_bound"></a>set_bound 

 Establece el número máximo de vínculos de origen que se pueden agregar a este `source_link_manager` objeto.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parámetros  
 `_MaxLinks`  
 El número máximo de vínculos.  
  
##  <a name="ctor"></a>source_link_manager) 

 Construye un objeto `source_link_manager`.  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a>~ source_link_manager) 

 Destruye el objeto `source_link_manager`.  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [single_link_registry (clase)](single-link-registry-class.md)   
 [multi_link_registry (clase)](multi-link-registry-class.md)
