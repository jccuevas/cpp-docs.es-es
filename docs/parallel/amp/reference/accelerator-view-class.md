---
title: accelerator_view (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amprt/Concurrency::accelerator_view
dev_langs:
- C++
helpviewer_keywords:
- accelerator_view class
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: 18
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
ms.openlocfilehash: 78569f1ff21af3ed05cb908a851f0fe05d5d271a
ms.lasthandoff: 02/24/2017

---
# <a name="acceleratorview-class"></a>accelerator_view (Clase)
Representa una abstracción del dispositivo virtual en un acelerador C++ AMP de datos en paralelo.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
class accelerator_view;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[accelerator_view (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `accelerator_view`.|  
|[~ accelerator_view (destructor)](#dtor)|Destruye el objeto `accelerator_view`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[create_marker (método)](#create_marker)|Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.|  
|[Flush (método)](#flush)|Envía todos los comandos pendientes en la cola de la `accelerator_view` objeto en el Acelerador para su ejecución.|  
|[get_accelerator (método)](#get_accelerator)|Devuelve el objeto `accelerator` para el objeto `accelerator_view`.|  
|[get_is_auto_selection (método)](#get_is_auto_selection)|Devuelve un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando la `accelerator_view` objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[get_is_debug (método)](#get_is_debug)|Devuelve un valor booleano que indica si la `accelerator_view` objeto tiene la capa de depuración habilitada para los informes de error importante.|  
|[get_queuing_mode (método)](#get_queuing_mode)|Devuelve el modo de cola para el `accelerator_view` objeto.|  
|[get_version (método)](#get_version)|Devuelve la versión de la `accelerator_view`.|  
|[Wait (método)](#wait)|Espera a que todos los comandos que se envían a la `accelerator_view` objeto que se va a finalizar.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador! = (operador)](#operator_neq)|Compara este `accelerator_view` objeto con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.|  
|[operador = (operador)](#operator_eq)|Copia el contenido del elemento `accelerator_view` objeto en éste.|  
|[Operator == (operador)](#operator_eq_eq)|Compara este `accelerator_view` objeto con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Acelerador de miembro de datos](#accelerator)|Obtiene el objeto `accelerator` para el objeto `accelerator_view`.|  
|[Miembro de datos de is_auto_selection](#is_auto_selection)|Obtiene un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando la `accelerator_view` objeto se pasa a un [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).|  
|[is_debug miembro de datos](#is_debug)|Obtiene un valor booleano que indica si la `accelerator_view` objeto tiene la capa de depuración habilitada para los informes de error importante.|  
|[queuing_mode (miembro de datos)](#queuing_mode)|Obtiene el modo de cola para el `accelerator_view` objeto.|  
|[Miembro de datos de la versión](#version)|Obtiene la versión del acelerador.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `accelerator_view`  
  
### <a name="remarks"></a>Comentarios  
 Un `accelerator_view` objeto representa una vista lógica, aislada de un acelerador. Un dispositivo de cálculo físico único puede tener muchos aislado, lógica `accelerator_view` objetos. Cada acelerador tiene un valor predeterminado `accelerator_view` objeto. Adicionales `accelerator_view` se pueden crear objetos.  
  
 Dispositivos físicos pueden compartirse entre varios subprocesos de cliente. Subprocesos de cliente forma cooperativa pueden utilizar el mismo `accelerator_view` objeto de un acelerador, o cada cliente puede comunicarse con un dispositivo de proceso a través de una independiente `accelerator_view` objeto para el aislamiento de otros subprocesos del cliente.  
  
 Un `accelerator_view` objeto puede tener uno de los dos [queuing_mode (enumeración)](concurrency-namespace-enums-amp.md#queuing_mode) Estados. Si el modo de cola es `immediate`, comandos como `copy` y `parallel_for_each` se envían al dispositivo acelerador correspondiente en cuanto se devuelven al llamador. Si el modo de cola es `deferred`, dichos comandos ponen en cola en una cola de comando que corresponde a la `accelerator_view` objeto. Comandos no se envían en realidad en el dispositivo hasta que `flush()` se llama.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amprt.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="a-nameacceleratora-accelerator"></a><a name="accelerator"></a>Acelerador 

Obtiene el objeto de aceleración para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_accelerator)) Concurrency::accelerator accelerator;  
```  
  
## <a name="a-namectora-acceleratorview"></a><a name="ctor"></a>accelerator_view 

Inicializa una nueva instancia de la clase accelerator_view copiando una existente `accelerator_view` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
accelerator_view( const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar.  
  
## <a name="a-nameacceleratorviewcreatemarkera-createmarker"></a><a name="accelerator_view__create_marker"></a>create_marker 

Devuelve un futuro para realizar un seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
concurrency::completion_future create_marker();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un futuro para realizar el seguimiento de la finalización de todos los comandos enviados hasta ahora a este `accelerator_view` objeto.  
  
## <a name="a-nameflusha-flush"></a><a name="flush"></a>Vaciar 

Envía que todos los comandos pendientes en cola para el objeto accelerator_view para el Acelerador para su ejecución.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void flush();  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  

## <a name="a-nameacceleratorviewgetacceleratora-getaccelerator"></a><a name="accelerator_view__get_accelerator"></a>get_accelerator 

Devuelve el objeto de aceleración para el objeto accelerator_view.
### <a name="syntax"></a>Sintaxis
```
accelerator get_accelerator() const;
```
### <a name="return-value"></a>Valor devuelto
El objeto de aceleración para el objeto accelerator_view.

## <a name="a-nameacceleratorviewgetisautoselectiona-getisautoselection"></a><a name="accelerator_view__get_is_auto_selection"></a>get_is_auto_selection 

Devuelve un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool get_is_auto_selection() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true`Si el tiempo de ejecución selecciona automáticamente un acelerador adecuado; de lo contrario, `false`.  
  
## <a name="a-nameacceleratorviewgetisdebuga-getisdebug"></a><a name="accelerator_view__get_is_debug"></a>get_is_debug 

Devuelve un valor booleano que indica si el objeto accelerator_view tiene la capa de depuración habilitada para los informes de error importante.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool get_is_debug() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un valor booleano que indica si la `accelerator_view` objeto tiene la capa de depuración habilitada para los informes de error importante.  

## <a name="a-nameacceleratorviewgetqueuingmodea-getqueuingmode"></a><a name="accelerator_view__get_queuing_mode"></a>get_queuing_mode 

Devuelve el modo de cola para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
queuing_mode get_queuing_mode() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de cola para el `accelerator_view` objeto.  
  
## <a name="a-nameacceleratorviewgetversiona-getversion"></a><a name="accelerator_view__get_version"></a>get_version 

Devuelve la versión de la accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
unsigned int get_version() const;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 La versión de la `accelerator_view`.  
  
## <a name="a-nameacceleratorviewisautoselectiona-isautoselection"></a><a name="accelerator_view__is_auto_selection"></a>is_auto_selection 

Obtiene un valor booleano que indica si el tiempo de ejecución selecciona automáticamente un acelerador adecuado cuando se pasa el accelerator_view a una [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each).  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_is_auto_selection)) bool is_auto_selection;  
```  
  
## <a name="a-nameacceleratorviewisdebuga-isdebug"></a><a name="accelerator_view__is_debug"></a>is_debug 

Obtiene un valor booleano que indica si el objeto accelerator_view tiene la capa de depuración habilitada para los informes de error importante.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_is_debug)) bool is_debug;  
```  
  
## <a name="a-nameacceleratorviewoperatorneqa-operator"></a><a name="accelerator_view__operator_neq"></a>operador! = 

Compara este objeto accelerator_view con otro y devuelve `false` si son iguales; en caso contrario, devuelve `true`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator!= (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `false` si los dos objetos son iguales; de lo contrario, `true`.  
  
## <a name="a-nameacceleratorviewoperatoreqa-operator"></a><a name="accelerator_view__operator_eq"></a>operador = 

Copia el contenido del objeto accelerator_view especificado en éste.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
accelerator_view & operator= (    const accelerator_view & _Other );  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a copiar de.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a la modificación `accelerator_view` objeto.  
  
## <a name="a-nameacceleratorviewoperatoreqeqa-operator"></a><a name="accelerator_view__operator_eq_eq"></a>operador == 

Compara este objeto accelerator_view con otro y devuelve `true` si son iguales; en caso contrario, devuelve `false`.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
bool operator= = (    const accelerator_view & _Other ) const;  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `accelerator_view` objeto que se va a comparar con éste.  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si los dos objetos son iguales; de lo contrario, `false`.  
  
## <a name="a-nameacceleratorviewqueuingmodea-queuingmode"></a><a name="accelerator_view__queuing_mode"></a>queuing_mode 

Obtiene el modo de cola para el objeto accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_queuing_mode)) Concurrency::queuing_mode queuing_mode;  
```  
  
## <a name="a-nameacceleratorviewversiona-version"></a><a name="accelerator_view__version"></a>Versión 

Obtiene la versión de la accelerator_view.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
__declspec(property(get= get_version)) unsigned int version;  
```  
  
## <a name="a-nameacceleratorviewwaita-wait"></a><a name="accelerator_view__wait"></a>esperar 

Espera a que todos los comandos enviados al objeto accelerator_view Finalizar.  
  
### <a name="syntax"></a>Sintaxis  
  
```  
void wait();  
```  
  
#### <a name="return-value"></a>Valor devuelto  
 Devuelve `void`.  
  
#### <a name="remarks"></a>Comentarios  
 Si el [queuing_mode](concurrency-namespace-enums-amp.md#queuing_mode) es `immediate`, este método vuelve inmediatamente sin bloquear.  
  
##  <a name="a-namedtora-acceleratorview"></a><a name="dtor"></a>~ accelerator_view 

 Destruye el objeto accelerator_view.  
  
#### <a name="syntax"></a>Sintaxis  
  
```  
~accelerator_view();  
```  
  
### <a name="return-value"></a>Valor devuelto  
  
 
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

