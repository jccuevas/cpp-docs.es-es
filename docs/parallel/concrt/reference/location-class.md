---
title: Location (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::location
dev_langs:
- C++
helpviewer_keywords:
- location class
ms.assetid: c3289f51-5bf1-4dff-a18d-d0dab8e5d9c7
caps.latest.revision: 10
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
ms.openlocfilehash: 1a404f44600addcbf332fabcfc19a7b48dab0c81
ms.lasthandoff: 02/24/2017

---
# <a name="location-class"></a>location (Clase)
Una abstracción de una ubicación física en el hardware.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class location;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[ubicación de Constructor](#ctor)|Sobrecargado. Construye un objeto `location`.|  
|[~ location (destructor)](#dtor)|Destruye un objeto `location`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Método actual](#current)|Devuelve un `location` objeto que representa el lugar más específico que se está ejecutando el subproceso que realiza la llamada.|  
|[from_numa_node (método)](#from_numa_node)|Devuelve un `location` el objeto que representa un nodo NUMA.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador! = (operador)](#operator_neq)|Determina si dos `location` objetos representan una ubicación diferente.|  
|[operador = (operador)](#operator_eq)|Asigna el contenido de otro `location` objeto a ésta.|  
|[Operator == (operador)](#operator_eq_eq)|Determina si dos `location` objetos representan la misma ubicación.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `location`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namedtora-location"></a><a name="dtor"></a>~ ubicación 

 Destruye un objeto `location`.  
  
```
~location();
```  
  
##  <a name="a-namecurrenta-current"></a><a name="current"></a>actual 

 Devuelve un `location` objeto que representa el lugar más específico que se está ejecutando el subproceso que realiza la llamada.  
  
```
static location __cdecl current();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una ubicación que representa el lugar más específica a la que está ejecutando el subproceso que realiza la llamada.  
  
##  <a name="a-namefromnumanodea-fromnumanode"></a><a name="from_numa_node"></a>from_numa_node 

 Devuelve un `location` el objeto que representa un nodo NUMA.  
  
```
static location __cdecl from_numa_node(unsigned short _NumaNodeNumber);
```  
  
### <a name="parameters"></a>Parámetros  
 `_NumaNodeNumber`  
 El número de nodos NUMA para construir una ubicación para.  
  
### <a name="return-value"></a>Valor devuelto  
 Una ubicación que representa el nodo NUMA especificado por el `_NumaNodeNumber` parámetro.  
  
##  <a name="a-namectora-location"></a><a name="ctor"></a>ubicación 

 Construye un objeto `location`.  
  
```
location();

location(
    const location& _Src);

location(
    T _LocationType,
    unsigned int _Id,
    unsigned int _BindingId = 0,
    _Inout_opt_ void* _PBinding = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Src`  
 `_LocationType`  
 `_Id`  
 `_BindingId`  
 `_PBinding`  
  
### <a name="remarks"></a>Comentarios  
 Una ubicación predeterminada construido representa el sistema como un todo.  
  
##  <a name="a-nameoperatorneqa-operator"></a><a name="operator_neq"></a>operador! = 

 Determina si dos `location` objetos representan una ubicación diferente.  
  
```
bool operator!= (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si son diferentes, las dos ubicaciones `false` en caso contrario.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Asigna el contenido de otro `location` objeto a ésta.  
  
```
location& operator= (const location& _Rhs);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
 Objeto `location` de origen.  
  
### <a name="return-value"></a>Valor devuelto  
  
##  <a name="a-nameoperatoreqeqa-operator"></a><a name="operator_eq_eq"></a>operador == 

 Determina si dos `location` objetos representan la misma ubicación.  
  
```
bool operator== (const location& _Rhs) const;
```  
  
### <a name="parameters"></a>Parámetros  
 `_Rhs`  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si las dos ubicaciones son idénticas, y `false` en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

