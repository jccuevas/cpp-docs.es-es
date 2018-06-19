---
title: NORM (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
dev_langs:
- C++
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f23ea5d40ecca7ee47d7eae659bfd3da286d8831
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705398"
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
|NORM::operator-||  
|NORM::operator:||  
|float NORM::operator|Operador de conversión. Convertir el número de la norma en flotante valor de punto.|  
|NORM::operator * =||  
|NORM::operator / =||  
|NORM::operator ++||  
|NORM::operator +=||  
|NORM::operator =||  
|NORM::operator =||  
  
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
