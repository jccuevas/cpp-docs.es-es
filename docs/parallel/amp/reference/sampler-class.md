---
title: Sampler (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
caps.latest.revision: 7
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
ms.openlocfilehash: 090e05e294646b7571a3d06ca8ed23583a306756
ms.lasthandoff: 02/24/2017

---
# <a name="sampler-class"></a>sampler (Clase)
Los agregados de clase muestra información de configuración que se usará para el muestreo de textura de muestreo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class sampler;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[muestrario de Constructor](#ctor)|Sobrecargado. Crea una instancia de la muestra.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[get_address_mode (método)](#get_address_mode)|Devuelve el `address_mode` asociado con el objeto de muestra.|  
|[get_border_color (método)](#get_border_color)|Devuelve el color del borde que está asociado con el objeto de muestra.|  
|[get_filter_mode (método)](#get_filter_mode)|Devuelve el `filter_mode` asociado con el objeto de muestra.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[operador = (operador)](#operator_eq)|Sobrecargado. Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[address_mode (miembro de datos)](#address_mode)|Obtiene el modo de direccionamiento de la `sampler` objeto.|  
|[Miembro de datos de border_color](#border_color)|Obtiene el color del borde de la `sampler` objeto.|  
|[filter_mode (miembro de datos)](#filter_mode)|Obtiene el modo de filtro de la `sampler` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `sampler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namectora-sampler"></a><a name="ctor"></a>muestra 

 Construye una instancia de la [Sampler (clase)](sampler-class.md).  
  
```  
sampler() restrict(cpu);

 *// [1] default constructor  
 
sampler(// [2] constructor  
    filter_mode _Filter_mode) restrict(cpu);

 
sampler(// [3] constructor  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [4] constructor  
    filter_mode _Filter_mode,  
    address_mode _Address_mode,  
    float_4 _Border_color = float_4(0.0f,
    0.0f,
    0.0f,
    0.0f)) restrict(cpu);

 
sampler(// [5] copy constructor  
    const sampler& _Other) restrict(amp,
    cpu);

 
sampler(// [6] move constructor  
    sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Filter_mode`  
 El modo de filtro que se utilizará para el muestreo.  
  
 `_Address_mode`  
 Modo de direccionamiento que se usará en el muestreo para todas las dimensiones.  
  
 `_Border_color`  
 El color del borde que se utilizará si el modo de dirección es address_border. El valor predeterminado es `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.  
  
 `_Other`  
 [5] Constructor de copias  
 El `sampler` objeto que se va a copiar en el nuevo `sampler` instancia.  
  
 [6] Constructor de movimiento  
 El `sampler` mover en el nuevo objeto `sampler` instancia.  
  
##  <a name="a-nameaddressmodea-addressmode"></a><a name="address_mode"></a>address_mode) 

 Obtiene el modo de direccionamiento de la `sampler` objeto.  
  
```  
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;  
```  
  
##  <a name="a-namebordercolora-bordercolor"></a><a name="border_color"></a>border_color 

 Obtiene el color del borde de la `sampler` objeto.  
  
```  
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;  
```  
  
##  <a name="a-namefiltermodea-filtermode"></a><a name="filter_mode"></a>filter_mode) 

 Obtiene el modo de filtro de la `sampler` objeto.  
  
```  
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;  
```  
  
##  <a name="a-namegetaddressmodea-getaddressmode"></a><a name="get_address_mode"></a>get_address_mode 

 Devuelve el modo de filtro que está configurado para este `sampler`.  
  
```  
Concurrency::graphics::address_mode get_address_mode() const __GPU;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de dirección que está configurado para la muestra.  
  
##  <a name="a-namegetbordercolora-getbordercolor"></a><a name="get_border_color"></a>get_border_color 

 Devuelve el color del borde que se configura para este `sampler`.  
  
```  
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Un float_4 que contiene el color del borde.  
  
##  <a name="a-namegetfiltermodea-getfiltermode"></a><a name="get_filter_mode"></a>get_filter_mode 

 Devuelve el modo de filtro que está configurado para este `sampler`.  
  
```  
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de filtro que está configurado para el Reproductor.  
  
##  <a name="a-nameoperatoreqa-operator"></a><a name="operator_eq"></a>operador = 

 Asigna el valor de otro objeto de muestra para una muestra existente.  
  
```  
sampler& operator= (// [1] copy assignment operator const sampler& _Other) restrict(amp,
    cpu);

 
sampler& operator= (// [2] move assingment operator sampler&& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 [1] operador de asignación de copia  
 El `sampler` objeto que se va a copiar en esta `sampler`.  
  
 [2] operador de asignación de movimiento de  
 El `sampler` mover este objeto `sampler`.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a esta instancia de muestra.  
  
## <a name="see-also"></a>Vea también  
 [Graphics Namespace](concurrency-graphics-namespace.md)

