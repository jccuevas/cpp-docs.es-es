---
title: end (Función)
ms.date: 01/22/2017
f1_keywords:
- collection/Windows::Foundation::Collections::end
helpviewer_keywords:
- end Function
ms.assetid: fb837bff-fc76-4bae-9096-facf0e03041c
ms.openlocfilehash: c46c601be2b2ed78cf79641a7fcf5324e615a771
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375813"
---
# <a name="end-function"></a>end (Función)

Devuelve un iterador que apunta más allá del final de una colección a la que se tiene acceso con el parámetro de interfaz especificado.

## <a name="syntax"></a>Sintaxis

```

template <typename T>
    ::Platform::Collections::VectorIterator<T>
    end(
        IVector<T>^ v       );

template <typename T>
    ::Platform::Collections::VectorViewIterator<T>
    end(
        IVectorView<T>^ v
       );
template <typename T>
    ::Platform::Collections::InputIterator<T>
    end(
        IIterable<T>^ i
       );
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
Un parámetro de tipo de plantilla.

*v*<br/>
Una colección de Vector\<T > o VectorView\<T > objetos que se accede mediante un IVector\<T >, o IVectorView\<T > interfaz.

*i*<br/>
Una colección de arbitrarios a Windows Runtime objetos que se tiene acceso mediante un IIterable\<T > interfaz.

### <a name="return-value"></a>Valor devuelto

Un iterador que apunta más allá del final de la colección.

### <a name="remarks"></a>Comentarios

Las dos primeras funciones de plantilla devuelven iteradores y la tercera función de plantilla devuelve un iterador de entrada.

El objeto [Platform::Collections::VectorViewIterator](../cppcx/platform-collections-vectorviewiterator-class.md) devuelto por `end` es un iterador de proxy que almacena elementos de tipo `VectorProxy<T>`. Sin embargo, el objeto proxy casi nunca está visible en el código del usuario. Para obtener más información, consulta [Colecciones (C++/CX)](../cppcx/collections-c-cx.md).

### <a name="requirements"></a>Requisitos

**Encabezado:** collection.h

**Espacio de nombres**: Windows::Foundation::Collections

## <a name="see-also"></a>Vea también

[Windows::Foundation::Collections (Espacio de nombres)](../cppcx/windows-foundation-collections-namespace-c-cx.md)
