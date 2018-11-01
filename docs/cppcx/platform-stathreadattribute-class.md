---
title: Platform::STAThreadAttribute (Clase)
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Platform
- COLLECTION/Platform::Platform::STAThreadAttribute constructor 1
- COLLECTION/Platform::Platform::STAThreadAttribute::Equals
- COLLECTION/Platform::Platform::STAThreadAttribute::GetHashCode
- COLLECTION/Platform::Platform::STAThreadAttribute::ToString
helpviewer_keywords:
- Platform::STAThreadAttribute Class
ms.assetid: f97960fc-e673-4d9e-910a-54c8415411c4
ms.openlocfilehash: 9073dc6e802aa2ed6bfa4fde2a09dd8a0864687b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555671"
---
# <a name="platformstathreadattribute-class"></a>Platform::STAThreadAttribute (Clase)

Indica que el modelo de subprocesamiento de una aplicación es un contenedor uniproceso (STA).

## <a name="syntax"></a>Sintaxis

```
public ref class STAThreadAttribute sealed : Attribute
```

### <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[STAThreadAttribute (Constructor 1)](#ctor)|Inicializa una nueva instancia de la clase.|

### <a name="public-methods"></a>Métodos públicos

El atributo STAThreadAttribute hereda de [Platform:: Object Class](../cppcx/platform-object-class.md). STAThreadAttribute también sobrecarga o tiene los siguientes miembros:

|nombre|Descripción|
|----------|-----------------|
|[STAThreadAttribute::Equals](#equals)|Determina si el objeto especificado es igual al objeto actual.|
|[STAThreadAttribute::GetHashCode](#gethashcode)|Devuelve el código hash de esta instancia.|
|[STAThreadAttribute::ToString](#tostring)|Devuelve una cadena que representa el objeto actual.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`Platform`

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres:** Plataforma

## <a name="ctor"></a> STAThreadAttribute constructor

Inicializa una nueva instancia de la clase STAThreadAttribute.

### <a name="syntax"></a>Sintaxis

```cpp
public:STAThreadAttribute();
```

## <a name="equals"></a> STAThreadAttribute::Equals

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

## <a name="gethashcode"></a> STAThreadAttribute::GetHashCode

Devuelve el código hash de esta instancia.

### <a name="syntax"></a>Sintaxis

```cpp
public:int GetHashCode();
```

### <a name="return-value"></a>Valor devuelto

Código hash de esta instancia.

## <a name="tostring"></a> STAThreadAttribute::ToString

Devuelve una cadena que representa el objeto actual.

### <a name="syntax"></a>Sintaxis

```cpp
public:String^ ToString();
```

### <a name="return-value"></a>Valor devuelto

Una cadena que representa el objeto actual.

## <a name="see-also"></a>Vea también

[Plataforma Namespace](platform-namespace-c-cx.md)