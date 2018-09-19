---
title: accelerator_view (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view
- AMPRT/accelerator_view
- AMPRT/Concurrency::accelerator_view:accelerator_view
- AMPRT/Concurrency::accelerator_view:create_marker
- AMPRT/Concurrency::accelerator_view:flush
- AMPRT/Concurrency::accelerator_view:get_accelerator
- AMPRT/Concurrency::accelerator_view:get_is_auto_selection
- AMPRT/Concurrency::accelerator_view:get_is_debug
- AMPRT/Concurrency::accelerator_view:get_queuing_mode
- AMPRT/Concurrency::accelerator_view:get_version
- AMPRT/Concurrency::accelerator_view:wait
- AMPRT/Concurrency::accelerator_view:accelerator
- AMPRT/Concurrency::accelerator_view:is_auto_selection
- AMPRT/Concurrency::accelerator_view:is_debug
- AMPRT/Concurrency::accelerator_view:queuing_mode
- AMPRT/Concurrency::accelerator_view:version
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 82ce81319212a833e66357cdf343489cb4108b67
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46084723"
---
# <a name="acceleratorview-class"></a>accelerator_view (Clase)
Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[accelerator_view Constructor](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view`.|  
|[~ accelerator_view (destructor)](#dtor)|Destruye el objeto `accelerator_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[create_marker](#create_marker)|Devuelve un valor futuro para realizar un seguimiento de la finalización de todos los comandos presentados hasta ahora a este `accelerator_view` objeto.|  
|[flush](#flush)|Envía todos los comandos pendientes en cola para el `accelerator_view` objeto para el Acelerador para su ejecución.|  
|[get_accelerator](#get_accelerator)|Devuelve el objeto `accelerator` para el objeto `accelerator_view`.|  
|[get_is_auto_selection](#get_is_auto_selection)|Devuelve un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando el `accelerator_view` objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[get_is_debug](#get_is_debug)|Devuelve un valor booleano que indica si el `accelerator_view` objeto tiene el nivel DEBUG habilitado para informar sobre errores.|  
|[get_queuing_mode](#get_queuing_mode)|Devuelve el modo de puesta en cola para el `accelerator_view` objeto.|  
|[get_version](#get_version)|Devuelve la versión de la `accelerator_view`.|  
|[Espere](#wait)|Espera a que todos los comandos enviados a la `accelerator_view` objeto que se va a finalizar.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator!=](#operator_neq)|Compara este `accelerator_view` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.|  
|[operator=](#operator_eq)|Copia el contenido del elemento especificado `accelerator_view` objeto en este.|  
|[operator==](#operator_eq_eq)|Compara este `accelerator_view` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Acelerador](#accelerator)|Obtiene el objeto `accelerator` para el objeto `accelerator_view`.|  
|[is_auto_selection](#is_auto_selection)|Obtiene un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando el `accelerator_view` objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[is_debug](#is_debug)|Obtiene un valor booleano que indica si el `accelerator_view` objeto tiene el nivel DEBUG habilitado para informar sobre errores.|  
|[queuing_mode](#queuing_mode)|Obtiene el modo de puesta en cola el `accelerator_view` objeto.|  
|[version](#version)|Obtiene la versión del acelerador.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `accelerator_view`  
  
### <a name="remarks"></a>Comentarios  
 Un `accelerator_view` objeto representa una vista aislada y lógica de un acelerador. Un dispositivo de proceso físicos solo puede tener muchos lógicos, aislados `accelerator_view` objetos. Cada acelerador tiene un valor predeterminado `accelerator_view` objeto. Adicionales `accelerator_view` se pueden crear objetos.  
  
 Dispositivos físicos pueden compartirse entre varios subprocesos de cliente. Subprocesos de cliente pueden utilizar cooperativamente el mismo `accelerator_view` objeto de un acelerador o cada cliente puede comunicarse con un dispositivo de proceso a través de una independiente `accelerator_view` objeto para el aislamiento de otros subprocesos de cliente.  
  
 Un `accelerator_view` objeto puede tener uno de los dos [queuing_mode (enumeración)](concurrency-namespace-enums-amp.md#queuing_mode) Estados. Si el modo de puesta en cola es `immediate`, comandos como `copy` y `parallel_for_each` se envían al dispositivo acelerador correspondiente en cuanto vuelven al llamador. Si el modo de puesta en cola es `deferred`, estos comandos se ponen en cola en una cola de comando que corresponde a la `accelerator_view` objeto. Los comandos no se envían realmente al dispositivo hasta que `flush()` se llama.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="accelerator"></a> Acelerador 

Obtiene el objeto Acelerador para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="ctor"></a> accelerator_view 

Inicializa una nueva instancia de la clase accelerator_view copiando existente `accelerator_view` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
*_Otro*<br/>
La `accelerator_view` objeto que se va a copiar.  
  
## <a name="accelerator_view__create_marker"></a> create_marker 

Devuelve un valor futuro para realizar un seguimiento de la finalización de todos los comandos presentados hasta ahora a este `accelerator_view` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro para realizar el seguimiento de la finalización de todos los comandos presentados hasta ahora a este `accelerator_view` objeto.  
  
## <a name="flush"></a> Vaciar 

Envía que todos los comandos pendientes en cola para el objeto accelerator_view para el Acelerador para su ejecución.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  

## <a name="accelerator_view__get_accelerator"></a> get_accelerator 

Devuelve el objeto Acelerador para el objeto accelerator_view.
### <a name="syntax"></a>Sintaxis
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Valor devuelto
El objeto Acelerador para el objeto accelerator_view.

## <a name="accelerator_view__get_is_auto_selection"></a> get_is_auto_selection 

Devuelve un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando accelerator_view se pase a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` Si el runtime seleccionará automáticamente un acelerador adecuado; en caso contrario, `false`.  
  
## <a name="accelerator_view__get_is_debug"></a> get_is_debug 

Devuelve un valor booleano que indica si el objeto accelerator_view tiene la capa DEBUG habilitada para informar sobre errores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si el `accelerator_view` objeto tiene el nivel DEBUG habilitado para informar sobre errores.  

## <a name="accelerator_view__get_queuing_mode"></a> get_queuing_mode 

Devuelve el modo de puesta en cola para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de puesta en cola para el `accelerator_view` objeto.  
  
## <a name="accelerator_view__get_version"></a> get_version 

Devuelve la versión de la accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator_view`.  
  
## <a name="accelerator_view__is_auto_selection"></a> is_auto_selection 

Obtiene un valor booleano que indica si el runtime seleccionará automáticamente un acelerador adecuado cuando accelerator_view se pase a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="accelerator_view__is_debug"></a> is_debug 

Obtiene un valor booleano que indica si el objeto accelerator_view tiene la capa DEBUG habilitada para informar sobre errores.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="accelerator_view__operator_neq"></a> operador! = 

Compara este objeto accelerator_view con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*_Otro*<br/>
La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false` si los dos objetos son iguales; de lo contrario, `true`.  
  
## <a name="accelerator_view__operator_eq"></a> operator= 

Copia el contenido del objeto accelerator_view especificado en este.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
*_Otro*<br/>
La `accelerator_view` objeto que se va a copiar desde.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la modificación `accelerator_view` objeto.  
  
## <a name="accelerator_view__operator_eq_eq"></a> operador == 

Compara este objeto accelerator_view con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
*_Otro*<br/>
La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los dos objetos son iguales; de lo contrario, `false`.  
  
## <a name="accelerator_view__queuing_mode"></a> queuing_mode 

Obtiene el modo de puesta en cola para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="accelerator_view__version"></a> Versión 

Obtiene la versión de la accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="accelerator_view__wait"></a> Espere 

Espera a que todos los comandos enviados al objeto accelerator_view Finalizar.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
#### <a name="remarks"></a>Comentarios  
 Si el [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) es `immediate`, este método regresa inmediatamente sin bloquear.  
  
##  <a name="dtor"></a> ~ accelerator_view 

 Destruye el objeto accelerator_view.  
  
#### <a name="syntax"></a>Sintaxis  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
 
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
