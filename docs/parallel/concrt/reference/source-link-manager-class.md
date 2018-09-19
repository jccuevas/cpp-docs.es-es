---
title: source_link_manager (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- source_link_manager class
ms.assetid: 287487cf-e0fe-4c35-aa3c-24f081d1ddae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff869fb93d5dae39a924c3d4133f5a6bc6fb824f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059802"
---
# <a name="sourcelinkmanager-class"></a>source_link_manager (Clase)
El objeto `source_link_manager` administra los vínculos de red del bloque de mensajería para los bloques `ISource`.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<class _LinkRegistry>
class source_link_manager;
```  
  
#### <a name="parameters"></a>Parámetros  
*_LinkRegistry*<br/>
El registro del vínculo de red.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|`const_pointer`|Un tipo que proporciona un puntero a un `const` elemento en un `source_link_manager` objeto.|  
|`const_reference`|Un tipo que proporciona una referencia a un `const` elemento almacenado en un `source_link_manager` objeto para leer y realizar operaciones const.|  
|`iterator`|Un tipo que proporciona un iterador que puede leer o modificar cualquier elemento de la `source_link_manager` objeto.|  
|`type`|El tipo de registro del vínculo está administrando mediante la `source_link_manager` objeto.|  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[source_link_manager](#ctor)|Construye un objeto `source_link_manager`.|  
|[~ source_link_manager (destructor)](#dtor)|Destruye el objeto `source_link_manager`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[add](#add)|Agrega un vínculo de origen a la `source_link_manager` objeto.|  
|[begin](#begin)|Devuelve un iterador al primer elemento en el `source_link_manager` objeto.|  
|[Contiene](#contains)|Busca el `network_link_registry` dentro de este `source_link_manager` objeto para un bloque especificado.|  
|[count](#count)|Cuenta el número de bloques vinculados el `source_link_manager` objeto.|  
|[reference](#reference)|Adquiere una referencia en el `source_link_manager` objeto.|  
|[register_target_block](#register_target_block)|Registra el bloque de destino que contiene este `source_link_manager` objeto.|  
|[release](#release)|Libera la referencia en el `source_link_manager` objeto.|  
|[remove](#remove)|Quita un vínculo desde el `source_link_manager` objeto.|  
|[set_bound](#set_bound)|Establece el número máximo de vínculos de origen que se pueden agregar a este `source_link_manager` objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Actualmente, los bloques de origen son cuentan las referencias. Éste es un contenedor en un `network_link_registry` objeto que permite el acceso simultáneo a los vínculos y proporciona la capacidad de hacer referencia a los vínculos a través de las devoluciones de llamada. Bloques de mensajes ( `target_block`s o `propagator_block`s) debe usar esta clase para sus vínculos de origen.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `source_link_manager`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** agents.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="add"></a> Agregar 

 Agrega un vínculo de origen a la `source_link_manager` objeto.  
  
```
void add(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se va a agregar.  
  
##  <a name="begin"></a> comenzar 

 Devuelve un iterador al primer elemento en el `source_link_manager` objeto.  
  
```
iterator begin();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un iterador que direcciona el primer elemento en el `source_link_manager` objeto.  
  
### <a name="remarks"></a>Comentarios  
 Indica el estado final del iterador por un `NULL` vínculo.  
  
##  <a name="contains"></a> Contiene 

 Busca el `network_link_registry` dentro de este `source_link_manager` objeto para un bloque especificado.  
  
```
bool contains(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se van a buscar en el `source_link_manager` objeto.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si se encontró el bloque especificado, `false` en caso contrario.  
  
##  <a name="count"></a> recuento 

 Cuenta el número de bloques vinculados el `source_link_manager` objeto.  
  
```
size_t count();
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de bloques vinculados el `source_link_manager` objeto.  
  
##  <a name="reference"></a> Referencia 

 Adquiere una referencia en el `source_link_manager` objeto.  
  
```
void reference();
```  
  
##  <a name="register_target_block"></a> register_target_block 

 Registra el bloque de destino que contiene este `source_link_manager` objeto.  
  
```
void register_target_block(_Inout_ ITarget<typename _Block::source_type>* _PTarget);
```  
  
### <a name="parameters"></a>Parámetros  
*_PTarget*<br/>
El bloque de destino que contiene este `source_link_manager` objeto.  
  
##  <a name="release"></a> Versión 

 Libera la referencia en el `source_link_manager` objeto.  
  
```
void release();
```  
  
##  <a name="remove"></a> Quitar 

 Quita un vínculo desde el `source_link_manager` objeto.  
  
```
bool remove(_EType _Link);
```  
  
### <a name="parameters"></a>Parámetros  
*_Vincular*<br/>
Un puntero a un bloque que se va a quitar, si se encuentra.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el vínculo ha encontrado y eliminado, `false` en caso contrario.  
  
##  <a name="set_bound"></a> set_bound 

 Establece el número máximo de vínculos de origen que se pueden agregar a este `source_link_manager` objeto.  
  
```
void set_bound(size_t _MaxLinks);
```  
  
### <a name="parameters"></a>Parámetros  
*_MaxLinks*<br/>
El número máximo de vínculos.  
  
##  <a name="ctor"></a> source_link_manager) 

 Construye un objeto `source_link_manager`.  
  
```
source_link_manager();
```  
  
##  <a name="dtor"></a> ~ source_link_manager) 

 Destruye el objeto `source_link_manager`.  
  
```
~source_link_manager();
```  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [single_link_registry (clase)](single-link-registry-class.md)   
 [multi_link_registry (clase)](multi-link-registry-class.md)
