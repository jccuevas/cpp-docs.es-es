---
title: NORM (clase) | Microsoft Docs
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
ms.openlocfilehash: 362ad3a2676fa1a7c8f965a6750782617d6a3203
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46425735"
---
# <a name="norm-class"></a>norm (Clase)

Representa un número de la norma. Cada elemento flotante es un número de punto en el intervalo de [-1, 0F, 1, 0F].

## <a name="syntax"></a>Sintaxis

```
class norm;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[NORM Constructor](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar en 0, 0f.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|NORM::operator-||
|NORM::operator--||
|NORM::operator float|Operador de conversión. Convertir el número de la norma en flotante valor de punto.|
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

Constructor predeterminado. Inicializar en 0, 0f.

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

*_V*<br/>
El valor utilizado para inicializar.

*_Otro*<br/>
El objeto usado para inicializar.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
