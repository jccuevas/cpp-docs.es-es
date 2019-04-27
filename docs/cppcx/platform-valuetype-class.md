---
title: Clase Platform::ValueType
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: 889cf3a53468491517d37978ca09472756ad9b7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62182956"
---
# <a name="platformvaluetype-class"></a>Clase Platform::ValueType

La clase base para las instancias de tipos de valor.

## <a name="syntax"></a>Sintaxis

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[ValueType::ToString](#tostring)|Devuelve una representación de cadena del objeto. Se hereda de [Platform:: Object](../cppcx/platform-object-class.md).|

### <a name="remarks"></a>Comentarios

La clase ValueType se usa para construir tipos de valor. ValueType se deriva de Object, que tiene miembros básicos. Sin embargo, el compilador desasocia esos miembros básicos de los tipos de valor que se derivan de la clase ValueType. El compilador vuelve a asociar esos miembros básicos cuando se encuadra un tipo de valor.

### <a name="requirements"></a>Requisitos

**Cliente mínimo admitido:** Windows 8

**Servidor mínimo admitido:** Windows Server 2012

**Espacio de nombres**: Plataforma

**Metadatos:** platform.winmd

## <a name="tostring"></a> Método ValueType

Devuelve una representación de cadena del objeto.

### <a name="syntax"></a>Sintaxis

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Valor devuelto

Un Platform que representa el valor.

## <a name="see-also"></a>Vea también

[Espacio de nombres de plataforma](../cppcx/platform-namespace-c-cx.md)
