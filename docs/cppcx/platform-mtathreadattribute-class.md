---
title: Platform::MTAThreadAttribute (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::MTAThreadAttribute::Equals
- VCCORLIB/Platform::MTAThreadAttribute::GetHashCode
- VCCORLIB/Platform::MTAThreadAttribute::ToString
helpviewer_keywords:
- Platform::MTAThreadAttribute Class
ms.assetid: bfc546a7-4333-4407-85b4-4721565e1f44
ms.openlocfilehash: 4564def412834ae0586292e8aa533d3b2bd0d679
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745261"
---
# <a name="platformmtathreadattribute-class"></a>Platform::MTAThreadAttribute (Clase)

Indica que el modelo de subprocesos de una aplicación es un contenedor multiproceso (MTA).

## <a name="syntax"></a>Sintaxis

```
public ref class MTAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[MTAThreadAttribute Constructor 1](#ctor) constructor|Inicializa una nueva instancia de la clase.|

### <a name="public-methods"></a>Métodos públicos

El atributo MTAThreadAttribute hereda de [Platform:: Object Class](../cppcx/platform-object-class.md). MTAThreadAttribute también sobrecarga o tiene los siguientes miembros:

|nombre|Descripción|
|----------|-----------------|
|[MTAThreadAttribute::Equals](#equals)|Determina si el objeto especificado es igual al objeto actual.|
|[MTAThreadAttribute::GetHashCode](#gethashcode)|Devuelve el código hash de esta instancia.|
|[MTAThreadAttribute::ToString](#tostring)|Devuelve una cadena que representa el objeto actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Platform`

### <a name="requirements"></a>Requisitos

**Metadatos:** platform.winmd

**Espacio de nombres**: Plataforma

## <a name="ctor"></a> MTAThreadAttribute (Constructor)

Inicializa una nueva instancia de la clase MTAThreadAttribute.

### <a name="syntax"></a>Sintaxis

```cpp
public:MTAThreadAttribute();
```

## <a name="equals"></a> MTAThreadAttribute::Equals

Determina si el objeto especificado es igual al objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
public:virtual override bool Equals( Object^ obj );
```

### <a name="parameters"></a>Parámetros

*obj*<br/>
Objeto que se va a comparar.

### <a name="return-value"></a>Valor devuelto

**True** si los objetos son iguales; en caso contrario, **false**.

## <a name="gethashcode"></a> MTAThreadAttribute::GetHashCode

Devuelve el código hash de esta instancia.

### <a name="syntax"></a>Sintaxis

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Código hash de esta instancia.

## <a name="tostring"></a> MTAThreadAttribute::ToString

Devuelve una cadena que representa el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Valor devuelto

Una cadena que representa el objeto actual.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)
