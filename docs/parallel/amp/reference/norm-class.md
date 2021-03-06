---
title: norm (Clase)
ms.date: 11/04/2016
f1_keywords:
- AMP_SHORT_VECTORS/norm
- AMP_SHORT_VECTORS/Concurrency::graphics::norm Constructor
ms.assetid: 73002f3d-c25e-4119-bcd3-4c46c9b6abf1
ms.openlocfilehash: b5740f33dea6aad79770f77f179803023432248a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447526"
---
# <a name="norm-class"></a>norm (Clase)

Representa un número de norma. Cada elemento es un número de punto flotante en el intervalo de [-1,0 f, 1.0 f].

## <a name="syntax"></a>Sintaxis

```cpp
class norm;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[norma (constructor)](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar en 0.0 f.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|norm::operator-||
|norm::operator--||
|norma:: Operator Float|Operador de conversión. Convierta el número de norma en un valor de punto flotante.|
|norm::operator*=||
|norm::operator/=||
|norma:: Operator + +||
|norm::operator+=||
|norm::operator=||
|norm::operator-=||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`norm`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_short_vectors. h

**Espacio de nombres:** Concurrency:: Graphics

## <a name="ctor"></a>norma

Constructor predeterminado. Inicializar en 0.0 f.

```cpp
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
Valor que se usa para inicializar.

*_Other*<br/>
Objeto usado para inicializar.

## <a name="see-also"></a>Consulte también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
