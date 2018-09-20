---
title: SafeInt::SafeInt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeInt::SafeInt
- SafeInt
- SafeInt.SafeInt
dev_langs:
- C++
helpviewer_keywords:
- SafeInt class, constructor
ms.assetid: 39e6f632-a396-40e6-9ece-cc3d4c5a78ef
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 723dbb3cec2281815c5733b8f2f0fff8f636a3a5
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402569"
---
# <a name="safeintsafeint"></a>SafeInt::SafeInt

Construye un **SafeInt** objeto.

## <a name="syntax"></a>Sintaxis

```cpp
SafeInt() throw

SafeInt (
   const T& i
) throw ()

SafeInt (
   bool b
) throw ()

template <typename U>
SafeInt (
   const SafeInt <U, E>& u
)

I template <typename U>
SafeInt (
   const U& i
)  
```

### <a name="parameters"></a>Parámetros

*i*<br/>
[in] El valor de la nueva **SafeInt** objeto. Debe ser un parámetro de tipo T o U, según el constructor.

*b*<br/>
[in] El valor booleano para la nueva **SafeInt** objeto.

*u*<br/>
[in] Un **SafeInt** de tipo U. El nuevo **SafeInt** objeto tendrá el mismo valor que *u*, pero serán de tipo T.

U el tipo de datos almacenados en el **SafeInt**. Esto puede ser el tipo de un valor booleano, carácter o entero. Si es un tipo entero, puede ser con o sin signo y tener entre 8 y 64 bits.

## <a name="remarks"></a>Comentarios

Para obtener más información acerca de los tipos de plantilla `T` y `E`, consulte [clase SafeInt](../windows/safeint-class.md).

El parámetro de entrada para el constructor, *i* o *u*, debe ser un tipo entero, carácter o un valor booleano. Si es otro tipo de parámetro, el **SafeInt** clase llamadas [static_assert](../cpp/static-assert.md) para indicar un parámetro de entrada no válido.

Los constructores que utilizan el tipo de plantilla `U` convertir automáticamente el parámetro de entrada para el tipo especificado por `T`. El **SafeInt** clase convierte los datos sin pérdida de datos. Notifica al controlador de errores `E` si no se puede convertir los datos al tipo `T` sin pérdida de datos.

Si creas un **SafeInt** desde un parámetro booleano, debe inicializar el valor inmediatamente. No se puede construir un **SafeInt** con el código `SafeInt<bool> sb;`. Esto generará un error de compilación.

## <a name="requirements"></a>Requisitos

**Encabezado:** safeint.h

**Namespace:** msl::utilities

## <a name="see-also"></a>Vea también

[Biblioteca SafeInt](../windows/safeint-library.md)<br/>
[SafeInt (clase)](../windows/safeint-class.md)<br/>
[SafeIntException (clase)](../windows/safeintexception-class.md)