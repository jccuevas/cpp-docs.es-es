---
title: NORM (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp_short_vectors/Concurrency::graphics::norm
dev_langs:
- C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
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
ms.openlocfilehash: 8ff5a99136a75d17d914783496205f1dd1eb4a06
ms.lasthandoff: 02/24/2017

---
# <a name="norm-class"></a>norm (Clase)
Representa un número de norma. Cada elemento flotante es un número de punto en el intervalo de [-1, 0F, 1.0f].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class norm;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[NORM Constructor](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar a 0, 0f.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|NORM::operator-(operador)||  
|NORM::operator--(operador)||  
|float NORM::operator (operador)|Operador de conversión. Convertir el número de la norma en flotante valor de punto.|  
|NORM::operator * = (operador)||  
|NORM::operator / = (operador)||  
|NORM::operator ++ (operador)||  
|NORM::operator += (operador)||  
|NORM::operator = (operador)||  
|NORM::operator-= (operador)||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `norm`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_short_vectors.h  
  
 **Namespace:** Graphics  
  
##  <a name="a-namectora-norm"></a><a name="ctor"></a>NORM 

 Constructor predeterminado. Inicializar a 0, 0f.  
  
```  
norm(
    void) restrict(amp,
    cpu);

 
explicit norm(
    float _V) restrict(amp,
    cpu);

 
explicit norm(
    unsigned int _V) restrict(amp,
    cpu);

 
explicit norm(
    int _V) restrict(amp,
    cpu);

 
explicit norm(
    double _V) restrict(amp,
    cpu);

 
norm(
    const norm& _Other) restrict(amp,
    cpu);

 
norm(
    const unorm& _Other) restrict(amp,
    cpu);
```  
  
### <a name="parameters"></a>Parámetros  
 `_V`  
 El valor que se utiliza para inicializar.  
  
 `_Other`  
 Objeto utilizado para inicializar.  
  
## <a name="see-also"></a>Vea también  
 [Graphics Namespace](concurrency-graphics-namespace.md)

