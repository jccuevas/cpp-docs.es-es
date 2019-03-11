---
title: begin (Función)
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::begin
helpviewer_keywords:
- begin Function
ms.assetid: 5a44fb33-e247-49fd-b7a1-4a5b42e9e1e4
ms.openlocfilehash: 1b95e4d32321aadf7de65ecb25109fbecd9eb614
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741410"
---
# <a name="begin-function"></a>begin (Función)

Devuelve un iterador que apunta al principio de una colección a la que se tiene acceso con el parámetro de interfaz especificado.

## <a name="syntax"></a>Sintaxis

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    begin(
          IVector<T>^ v         );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    begin(
          IVectorView<T>^ v
         );

template <typename T>
    ::Platform::Collections::InputIterator<T>
    begin(
          IIterable<T>^ i         );
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un parámetro de tipo de plantilla.

*v*<br/>
Una colección de Vector\<T > o VectorView\<T > objetos que se accede mediante un IVector\<T > o IVectorView\<T > interfaz.

*i*<br/>
Una colección de objetos arbitrarios de Windows en tiempo de ejecución que se accede mediante un IIterable\<T > interfaz.

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta al principio de la colección.

### <a name="remarks"></a>Comentarios

Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.

El objeto VectorIterator objeto devuelto por begin es un iterador de proxy que almacena elementos de tipo VectorProxy\<T >. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Windows::Foundation::Collections

## <a name="see-also"></a>Vea también

[Collections Namespace](../cppcx/windows-foundation-collections-namespace-c-cx.md)
