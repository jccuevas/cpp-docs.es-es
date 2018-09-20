---
title: unorm (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- unorm
- AMP_SHORT_VECTORS/unorm
- AMP_SHORT_VECTORS/Concurrency::graphics::unorm Constructor
dev_langs:
- C++
ms.assetid: bc30bd20-6452-4d5f-9158-3b11c4c16ed2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 131a928c5943ab9bf4dcc327b044d76e5646ede7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377388"
---
# <a name="unorm-class"></a>unorm (Clase)

Representa un número unorm. Cada elemento flotante es un número de punto en el intervalo de [0, 0F, 1, 0F].

## <a name="syntax"></a>Sintaxis

```
class unorm;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[unorm (Constructor)](#ctor)|Sobrecargado. Constructor predeterminado. Inicializar en 0, 0f.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|unorm::operator--||
|unorm::operator float|Operador de conversión. Convertir el número de unorm en flotante valor de punto.|
|unorm::operator * =||
|unorm::operator / =||
|unorm::operator ++||
|unorm::operator +=||
|unorm::operator =||
|unorm::operator =||

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`unorm`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp_short_vectors.h

**Namespace:** Concurrency:: Graphics

##  <a name="ctor"></a> unorm

Constructor predeterminado. Inicializar en 0, 0f.

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

*_V*<br/>
El valor utilizado para inicializar.

*_Otro*<br/>
El objeto norma usado para inicializar.

## <a name="see-also"></a>Vea también

[Concurrency::graphics (espacio de nombres)](concurrency-graphics-namespace.md)
