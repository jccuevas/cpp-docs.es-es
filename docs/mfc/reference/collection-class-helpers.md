---
title: Asistentes de clase de colección
ms.date: 11/04/2016
f1_keywords:
- vc.mfc.macros.classes
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 3992e6c0cf25925e01858016e4bac93d5552fe8b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57266151"
---
# <a name="collection-class-helpers"></a>Asistentes de clase de colección

Las clases de colección `CMap`, `CList`, y `CArray` usar funciones de aplicación auxiliar con plantilla global para estos fines, como comparar, copiar y serializar los elementos. Como parte de la implementación de clases basadas en `CMap`, `CList`, y `CArray`, debe invalidar estas funciones según sea necesario con las versiones adaptadas al tipo de datos almacenados en el mapa, lista o matriz. Para obtener información sobre cómo reemplazar las funciones auxiliares como `SerializeElements`, consulte el artículo [colecciones: Cómo crear una colección con seguridad de tipos](../../mfc/how-to-make-a-type-safe-collection.md). Tenga en cuenta que `ConstructElements` y `DestructElements` han quedado en desuso.

La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales en afxtempl.h que le ayudarán a personalizar sus clases de colección:

### <a name="collection-class-helpers"></a>Asistentes de clase de colección

|||
|-|-|
|[CompareElements](#compareelements)|Indica si los elementos son iguales.|
|[CopyElements](#copyelements)|Copia los elementos de una matriz a otra.|
|[DumpElements](#dumpelements)|Proporciona los resultados de diagnóstico orientados a secuencia.|
|[HashKey](#hashkey)|Calcula una clave hash.|
|[SerializeElements](#serializeelements)|Almacena o recupera los elementos hacia o desde un archivo.|

##  <a name="compareelements"></a>  CompareElements

Llamadas directas [CList::Find] (clist class.md #not_found.md #clist__find e indirectamente por [cmap__lookup](cmap-class.md#lookup) y [cmap__operator &#91; &#93; ](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
El tipo del primer elemento que se va a comparar.

*pElement1*<br/>
Puntero al primer elemento que se va a comparar.

*ARG_TYPE*<br/>
El tipo del segundo elemento que se va a comparar.

*pElement2*<br/>
Puntero al segundo elemento que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto señalado por *pElement1* es igual que el objeto al que señala *pElement2*; de lo contrario, 0.

### <a name="remarks"></a>Comentarios

El `CMap` llama a usar el `CMap` parámetros de plantilla *clave* y *ARG_KEY*.

La implementación predeterminada devuelve el resultado de la comparación de  *\*pElement1* y  *\*pElement2*. Reemplace esta función para que compare los elementos de una manera que sea adecuada para su aplicación.

El lenguaje C++ define el operador de comparación ( `==`) para los tipos simples (**char**, **int**, **float**, etc.) pero no define un operador de comparación para las clases y estructuras. Si desea usar `CompareElements` o para crear una instancia de una de las clases de colección que lo utiliza, debe definir el operador de comparación o sobrecarga `CompareElements` con una versión que devuelve los valores adecuados.

### <a name="requirements"></a>Requisitos

   **Encabezado:** afxtempl.h

##  <a name="copyelements"></a>  CopyElements

Esta función se invoca directamente por [CArray::Append](carray-class.md#append) y [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Parámetro de plantilla que especifica el tipo de elementos que se copiarán.

*pDest*<br/>
Puntero a la que se copiarán los elementos de destino.

*pSrc*<br/>
Puntero al origen de los elementos que se va a copiar.

*nCount*<br/>
Número de elementos que se copiarán.

### <a name="remarks"></a>Comentarios

La implementación predeterminada usa el operador de asignación simple ( **=** ) para realizar la operación de copia. Si el tipo que se copia no tiene un operador sobrecargado =, la implementación predeterminada realiza una copia bit a bit.

Para obtener información sobre la implementación de esta y otras funciones auxiliares, consulte el artículo [colecciones: Cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

##  <a name="dumpelements"></a>  DumpElements

Para los elementos de la colección cuando se invalida, proporciona orientado a secuencias de salida de diagnóstico en forma de texto.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*dc*<br/>
Contexto para volcar los elementos de volcado de memoria.

*TYPE*<br/>
Especifica el tipo de los elementos de un parámetro de plantilla.

*pElements*<br/>
Puntero a los elementos que se va a volcar.

*nCount*<br/>
Número de elementos que se va a volcar.

### <a name="remarks"></a>Comentarios

El `CArray::Dump`, `CList::Dump`, y `CMap::Dump` funciones llamar si la profundidad del volcado de memoria es mayor que 0.

La implementación predeterminada no hace nada. Si se derivan de los elementos de la colección `CObject`, la invalidación normalmente creará una iteración por los elementos de la colección, una llamada a `Dump` para cada elemento a su vez.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

##  <a name="hashkey"></a>  HashKey

Calcula un valor hash para la clave especificada.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parámetros

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo de datos utilizado para tener acceso a las claves del mapa.

*key*<br/>
Clave cuyo valor hash se calcula.

### <a name="return-value"></a>Valor devuelto

El valor de clave hash.

### <a name="remarks"></a>Comentarios

Esta función se invoca directamente por [CMap::RemoveKey](cmap-class.md#removekey) e indirectamente por [CMap::Lookup](cmap-class.md#lookup) y [CMap::Operator &#91; &#93; ](cmap-class.md#operator_at).

La implementación predeterminada crea un valor hash trasladando *clave* derecha por cuatro posiciones. Reemplace esta función para que devuelva valores hash adecuada para su aplicación.

### <a name="example"></a>Ejemplo

```cpp
template <> UINT AFXAPI HashKey(unsigned __int64 key)
{
   // Generate the hash value by XORing the lower 32 bits of the number
   // with the upper 32 bits
   return(UINT(key) ^ UINT(key >> 32));
}
```

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

##  <a name="serializeelements"></a>  SerializeElements

[CArray](carray-class.md), [CList](clist-class.md), y [CMap](cmap-class.md) llame a esta función para serializar los elementos.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*TYPE*<br/>
Especifica el tipo de los elementos de un parámetro de plantilla.

*ar*<br/>
Un objeto de almacenamiento para archivar o salientes.

*pElements*<br/>
Puntero a los elementos que se archivan.

*nCount*<br/>
Número de elementos que se va a archivar

### <a name="remarks"></a>Comentarios

La implementación predeterminada no bit a bit de lectura o escritura.

Para obtener información sobre la implementación de esta y otras funciones auxiliares, consulte el artículo [colecciones: Cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).

### <a name="example"></a>Ejemplo

Vea el ejemplo en el artículo [colecciones: Cómo crear una colección con seguridad de tipos](../how-to-make-a-type-safe-collection.md).

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

## <a name="see-also"></a>Vea también

[Macros y funciones globales](mfc-macros-and-globals.md)<br/>
[CMap (clase)](cmap-class.md)<br/>
[CList (clase)](clist-class.md)<br/>
[CArray (clase)](carray-class.md)
