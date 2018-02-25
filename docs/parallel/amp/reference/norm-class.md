---
title: NORM (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs:
- C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d462b023d85222601d0f5c59b6b256ff525c7985
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="norm-class"></a>norm (Clase)
Representa un número de norma. Cada elemento flotante es un número de punto en el intervalo de [-1.0f, 1.0f].  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class norm;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[NORM Constructor](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar que 0,0 f.|  
  
### <a name="public-operators"></a>Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|norm::operator-||  
|norm::operator--||  
|float NORM::operator|Operador de conversión. Convertir el número de la norma en flotante valor de punto.|  
|norm::operator*=||  
|norm::operator/=||  
|norm::operator++||  
|norm::operator+=||  
|norm::operator=||  
|norm::operator-=||  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `norm`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp_short_vectors.h  
  
 **Namespace:** Concurrency:: Graphics  
  
##  <a name="ctor"></a> NORM 

 Constructor predeterminado. Inicializar que 0,0 f.  
  
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
 El valor utilizado para inicializar.  
  
 `_Other`  
 El objeto utilizado para inicializar.  
  
## <a name="see-also"></a>Vea también  
 [Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
