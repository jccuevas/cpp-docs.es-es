---
title: unorm (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::unorm
- amp/Concurrency::graphics::unorm
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: aae5de80bed3b2d3d5c15285c2d12f2f6771a251
ms.lasthandoff: 02/24/2017

---
# <a name="unorm-class"></a>unorm (Clase)
Representa un número unorm. Cada elemento flotante es un número de punto en el rango de [0, 0F, 1.0f].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class unorm;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[unorm (Constructor)](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar a 0, 0f.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|unorm::operator--(operador)||  
|float unorm::operator (operador)|Operador de conversión. Convertir el número de unorm en flotante valor de punto.|  
|unorm::operator * = (operador)||  
|unorm::operator / = (operador)||  
|unorm::operator ++ (operador)||  
|unorm::operator += (operador)||  
|unorm::operator = (operador)||  
|unorm::operator-= (operador)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `unorm`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_short_vectors.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namectora-unorm"></a><a name="ctor"></a>unorm 

 Constructor predeterminado. Inicializar a 0, 0f.  
  
```  
unorm(
    void) restrict(amp,
    cpu);

 
explicit unorm(
    float _V) restrict(amp,
    cpu);

 
explicit unorm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit unorm(
    int _V) restrict(amp,
    cpu);

 
explicit unorm(
    double _V) restrict(amp,
    cpu);

 
unorm(
    const unorm& _Other) restrict(amp,
    cpu);

 
inline explicit unorm(
    const norm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_V`  
 El valor que se utiliza para inicializar.  
  
 `_Other`  
 El objeto norm utilizado para inicializar.  
  
## <a name="see-also"></a>Vea también  
 [Graphics Namespace](concurrency-graphics-namespace.md)

