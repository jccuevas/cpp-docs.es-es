---
title: Sampler (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- sampler
- AMP_GRAPHICS/sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::sampler
- AMP_GRAPHICS/concurrency::sampler::graphics::get_address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::get_border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::get_filter_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::address_mode
- AMP_GRAPHICS/concurrency::sampler::graphics::border_color
- AMP_GRAPHICS/concurrency::sampler::graphics::filter_mode
dev_langs:
- C++
ms.assetid: 9a6a9807-497d-402d-b092-8c4d86275b80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f9788b62385f7c6f5eb82e3fbc69d63d3120cc2
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="sampler-class"></a>sampler (Clase)
Los agregados de clase muestra información de configuración que se usará para el muestreo de textura de muestreo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class sampler;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[muestra de Constructor](#ctor)|Sobrecargado. Crea una instancia de muestra.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[get_address_mode](#get_address_mode)|Devuelve el `address_mode` que ha asociado al objeto de muestra.|  
|[get_border_color](#get_border_color)|Devuelve el color del borde que esté asociada con el objeto de muestra.|  
|[get_filter_mode](#get_filter_mode)|Devuelve el `filter_mode` que ha asociado al objeto de muestra.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[operator=](#operator_eq)|Sobrecargado. Operador de asignación.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[address_mode](#address_mode)|Obtiene el modo de direccionamiento de la `sampler` objeto.|  
|[border_color](#border_color)|Obtiene el color del borde de la `sampler` objeto.|  
|[filter_mode](#filter_mode)|Obtiene el modo de filtro de la `sampler` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `sampler`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_graphics.h  
  
 **Namespace:** Concurrency:: Graphics  
  
##  <a name="ctor"></a> muestra 

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
 El modo de filtro que se usará en el muestreo.  
  
 `_Address_mode`  
 El modo de direccionamiento que se usará en el muestreo para todas las dimensiones.  
  
 `_Border_color`  
 El color del borde que se utilizará si el modo de direccionamiento es address_border. El valor predeterminado es `float_4(0.0f, 0.0f, 0.0f, 0.0f)`.  
  
 `_Other`  
 [5] Constructor de copias  
 El `sampler` objeto que se copiará en el nuevo `sampler` instancia.  
  
 [6] Constructor de movimiento  
 El `sampler` objeto al que desplazarse en el nuevo `sampler` instancia.  
  
##  <a name="address_mode"></a> address_mode 

 Obtiene el modo de direccionamiento de la `sampler` objeto.  
  
```  
__declspec(property(get= get_address_mode)) Concurrency::graphics::address_mode address_mode;  
```  
  
##  <a name="border_color"></a> border_color 

 Obtiene el color del borde de la `sampler` objeto.  
  
```  
__declspec(property(get= get_border_color)) Concurrency::graphics::float_4 border_color;  
```  
  
##  <a name="filter_mode"></a> filter_mode 

 Obtiene el modo de filtro de la `sampler` objeto.  
  
```  
__declspec(property(get= get_filter_mode)) Concurrency::graphics::filter_mode filter_mode;  
```  
  
##  <a name="get_address_mode"></a> get_address_mode 

 Devuelve el modo de filtro que está configurado para este `sampler`.  
  
```  
Concurrency::graphics::address_mode get_address_mode() const __GPU;  
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de direccionamiento que está configurado para la muestra.  
  
##  <a name="get_border_color"></a> get_border_color 

 Devuelve el color del borde que se configura para este `sampler`.  
  
```  
Concurrency::graphics::float_4 get_border_color() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Float_4 que contiene el color del borde.  
  
##  <a name="get_filter_mode"></a> get_filter_mode 

 Devuelve el modo de filtro que está configurado para este `sampler`.  
  
```  
Concurrency::graphics::filter_mode get_filter_mode() const restrict(amp, cpu);
```  
  
### <a name="return-value"></a>Valor devuelto  
 El modo de filtro que está configurado para la muestra.  
  
##  <a name="operator_eq"></a> operator= 

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
 El `sampler` objeto al que desplazarse en esta `sampler`.  
  
### <a name="return-value"></a>Valor devuelto  
 Una referencia a esta instancia de muestra.  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
