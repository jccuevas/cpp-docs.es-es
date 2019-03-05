---
title: norm (Clase)
ms.date: 11/04/2016
f1_keywords:
- norm
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: 56f879ef2fc0d3010ab4f64fedaf2570dac565d1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272430"
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
|norm::operator-||
|norm::operator--||
|NORM::operator float|Operador de conversión. Convertir el número de la norma en flotante valor de punto.|
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

**Espacio de nombres**: Concurrency:: Graphics

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

*_Other*<br/>
El objeto usado para inicializar.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
