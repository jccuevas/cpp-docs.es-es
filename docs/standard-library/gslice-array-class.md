---
title: gslice_array (Clase)
ms.date: 11/04/2016
f1_keywords:
- valarray/std::gslice_array
helpviewer_keywords:
- gslice_array class
ms.assetid: ad1b4514-b14a-4baf-a293-d5a8e8674c75
ms.openlocfilehash: 68ce774128395e941ff80580a02c4ee28a74a4e4
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689596"
---
# <a name="gslice_array-class"></a>gslice_array (Clase)

Una plantilla de clase auxiliar interna que admite objetos de segmentos generales proporcionando operaciones entre matrices de subconjuntos definidas por el segmento general de un valarray.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Type>
class gslice_array : public gsplice {
public:
    typedef Type value_type;
    void operator=(const valarray<Type>& x) const;

    void operator=(const Type& x) const;

    void operator*=(const valarray<Type>& x) const;

    void operator/=(const valarray<Type>& x) const;

    void operator%=(const valarray<Type>& x) const;

    void operator+=(const valarray<Type>& x) const;

    void operator-=(const valarray<Type>& x) const;

    void operator^=(const valarray<Type>& x) const;

    void operator&=(const valarray<Type>& x) const;

    void operator|=(const valarray<Type>& x) const;

    void operator<<=(const valarray<Type>& x) const;

    void operator>>=(const valarray<Type>& x) const;

// The rest is private or implementation defined
}
```

## <a name="remarks"></a>Comentarios

La clase describe un objeto que almacena una referencia a un objeto `va` de la clase [valarray](../standard-library/valarray-class.md)  **\<Type >** , junto con un objeto `gs` de la clase [GSlice](../standard-library/gslice-class.md) , que describe la secuencia de elementos que se va a seleccionar en el objeto `valarray<Type>`.

Solo se crea un objeto `gslice_array<Type>` escribiendo una expresión con el formato [va&#91;GS&#93;](../standard-library/valarray-class.md#op_at). Las funciones miembro de la clase gslice_array se comportarán como las signaturas de función correspondientes definidas para `valarray<Type>`, excepto en que solo la secuencia de elementos seleccionados se ve afectada.

La plantilla de clase se crea indirectamente mediante ciertas operaciones de valarray y no se puede usar directamente en el programa. En su lugar, el operador de subíndice de segmento utiliza una plantilla de clase auxiliar interna:

`gslice_array`\< **Type**> `valarray`\< **Type**>:: `operator[]` ( **constgslice&** ).

Solo se construye un objeto `gslice_array<Type>` escribiendo una expresión con el formato `va[gsl]`, para un segmento `gsl` de la `va` valarray. Las funciones miembro de la clase gslice_array se comportarán como las signaturas de función correspondientes definidas para `valarray<Type>`, excepto en que solo la secuencia de elementos seleccionados se ve afectada. La secuencia controlada por gslice_array se define mediante los tres parámetros del constructor de segmento, el índice del primer elemento en el primer segmento, el número de elementos en cada segmento y la distancia entre los elementos de cada segmento.

En el ejemplo siguiente:

```cpp
const size_t lv[] = {2, 3};
const size_t dv[] = {7, 2};
const valarray<size_t> len(lv, 2), str(dv, 2);

// va[gslice(3, len, str)] selects elements with
//   indices 3, 5, 7, 10, 12, 14
```

Los índices deben ser válidos para que el procedimiento sea válido.

## <a name="example"></a>Ejemplo

Vea el ejemplo de [gslice::gslice](../standard-library/gslice-class.md#gslice) para obtener un ejemplo de cómo declarar y usar una slice_array.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<valarray>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[Seguridad para subprocesos en la biblioteca estándar de C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
