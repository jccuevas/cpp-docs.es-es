---
title: Asistentes de clase de colección
ms.date: 11/04/2016
helpviewer_keywords:
- DestructElements function
- ConstructElements function
- SerializeElements function
- collection classes [MFC], helper functions
- helper functions collection class [MFC]
ms.assetid: bc3a2368-9edd-4748-9e6a-13cba79517ca
ms.openlocfilehash: 05fe49a4d8e6de92c584d40f3871f3efb906c7c8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374816"
---
# <a name="collection-class-helpers"></a>Asistentes de clase de colección

Las `CMap`clases `CList`de `CArray` colección , , y utilizar funciones auxiliares globales con plantilla para fines tales como comparar, copiar y serializar elementos. Como parte de la implementación `CList`de `CArray`clases basadas en `CMap`, , y , debe invalidar estas funciones según sea necesario con versiones adaptadas al tipo de datos almacenados en el mapa, lista o matriz. Para obtener información sobre cómo `SerializeElements`reemplazar funciones auxiliares como , vea el artículo [Colecciones: Cómo crear una colección segura](../../mfc/how-to-make-a-type-safe-collection.md)de tipos . Tenga `ConstructElements` en `DestructElements` cuenta que y han quedado en desuso.

La biblioteca Microsoft Foundation Class proporciona las siguientes funciones globales en afxtempl.h para ayudarle a personalizar las clases de colección:

### <a name="collection-class-helpers"></a>Asistentes de clase de colección

|||
|-|-|
|[CompareElements](#compareelements)|Indica si los elementos son los mismos.|
|[CopyElements](#copyelements)|Copia elementos de una matriz a otra.|
|[DumpElements](#dumpelements)|Proporciona una salida de diagnóstico orientada a secuencias.|
|[HashKey](#hashkey)|Calcula una clave hash.|
|[SerializeElements](#serializeelements)|Almacena o recupera elementos a o desde un archivo.|

## <a name="compareelements"></a><a name="compareelements"></a>CompareElements

Llamado directamente por [CList::Find](clist-class.md-not_found.md-clist__find e indirectamente por [cmap__lookup](cmap-class.md#lookup) y [cmap__operator &#91;&#93;](cmap-class.md#operator_at).

```
template<class TYPE, class ARG_TYPE>
BOOL AFXAPI
CompareElements(
    const TYPE* pElement1,
    const ARG_TYPE* pElement2);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
El tipo del primer elemento que se va a comparar.

*pElement1*<br/>
Puntero al primer elemento que se va a comparar.

*ARG_TYPE*<br/>
El tipo del segundo elemento que se va a comparar.

*pElement2*<br/>
Puntero al segundo elemento que se va a comparar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto al que apunta *pElement1* es igual al objeto al que apunta *pElement2*; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Las `CMap` llamadas `CMap` utilizan los parámetros de plantilla *KEY* y *ARG_KEY*.

La implementación predeterminada devuelve el resultado de la comparación de * \*pElement1* y * \*pElement2*. Invalide esta función para que compare los elementos de una manera que sea adecuada para la aplicación.

El lenguaje C++ define `==`el operador de comparación ( ) para tipos simples (**char**, **int**, **float**, etc.), pero no define un operador de comparación para clases y estructuras. Si desea usar `CompareElements` o crear instancias de una de las clases de `CompareElements` colección que la usa, debe definir el operador de comparación o la sobrecarga con una versión que devuelva los valores adecuados.

### <a name="requirements"></a>Requisitos

   **Encabezado:** afxtempl.h

## <a name="copyelements"></a><a name="copyelements"></a>CopyElements

Esta función es llamada directamente por [CArray::Append](carray-class.md#append) y [CArray::Copy](carray-class.md#copy).

```
template<class TYPE>
void AFXAPI CopyElements(
    TYPE* pDest,
    const TYPE* pSrc,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de elementos que se van a copiar.

*pDest*<br/>
Puntero al destino donde se copiarán los elementos.

*pSrc*<br/>
Puntero al origen de los elementos que se van a copiar.

*nCount*<br/>
Número de elementos que se van a copiar.

### <a name="remarks"></a>Observaciones

La implementación predeterminada utiliza **=** el operador de asignación simple ( ) para realizar la operación de copia. Si el tipo que se está copiando no tiene un operador sobrecargado, la implementación predeterminada realiza una copia bit a bit.

Para obtener información sobre cómo implementar esta y otras funciones auxiliares, vea el artículo [Colecciones: cómo crear una colección segura](../how-to-make-a-type-safe-collection.md)de tipos .

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

## <a name="dumpelements"></a><a name="dumpelements"></a>DumpElements

Proporciona una salida de diagnóstico orientada a secuencias en forma de texto para los elementos de la colección cuando se invalida.

```
template<class TYPE>
void  AFXAPI DumpElements(
    CDumpContext& dc,
    const TYPE* pElements,
    INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*Dc*<br/>
Contexto de volcado para elementos de volcado.

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos.

*pElements*<br/>
Puntero a los elementos que se van a volcar.

*nCount*<br/>
Número de elementos a volcar.

### <a name="remarks"></a>Observaciones

Las `CArray::Dump` `CList::Dump`funciones `CMap::Dump` , , y llaman a esto si la profundidad del volcado es mayor que 0.

La implementación predeterminada no hace nada. Si los elementos de la `CObject`colección se derivan de , la invalidación `Dump` normalmente recorrerá en iteración los elementos de la colección, llamando a cada elemento a su vez.

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

## <a name="hashkey"></a><a name="hashkey"></a>HashKey

Calcula un valor hash para la clave dada.

```
template<class ARG_KEY>
AFX_INLINE UINT AFXAPI HashKey(ARG_KEY  key);
```

### <a name="parameters"></a>Parámetros

*ARG_KEY*<br/>
Parámetro de plantilla que especifica el tipo de datos utilizado para acceder a las claves de mapa.

*key*<br/>
La clave cuyo valor hash se va a calcular.

### <a name="return-value"></a>Valor devuelto

El valor hash de la clave.

### <a name="remarks"></a>Observaciones

[CMap::RemoveKey](cmap-class.md#removekey) e indirectamente [cMap::Lookup](cmap-class.md#lookup) y [CMap::Operator &#91;&#93;](cmap-class.md#operator_at)llama a esta función directamente.

La implementación predeterminada crea un valor hash desplazando la *tecla* derecha por cuatro posiciones. Invalide esta función para que devuelva valores hash adecuados para la aplicación.

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

## <a name="serializeelements"></a><a name="serializeelements"></a>SerializeElements

[CArray](carray-class.md), [CList](clist-class.md)y [CMap](cmap-class.md) llaman a esta función para serializar elementos.

```
template<class TYPE>
void AFXAPI SerializeElements(CArchive& ar, TYPE* pElements, INT_PTR nCount);
```

### <a name="parameters"></a>Parámetros

*TIPO*<br/>
Parámetro de plantilla que especifica el tipo de los elementos.

*ar*<br/>
Objeto de archivo desde el que archivar.

*pElements*<br/>
Puntero a los elementos que se están archivando.

*nCount*<br/>
Número de elementos que se están archivando

### <a name="remarks"></a>Observaciones

La implementación predeterminada realiza una lectura o escritura bit a bit.

Para obtener información sobre cómo implementar esta y otras funciones auxiliares, vea el artículo [Colecciones: cómo crear una colección segura](../how-to-make-a-type-safe-collection.md)de tipos .

### <a name="example"></a>Ejemplo

Vea el ejemplo del artículo [Colecciones: Cómo crear una colección con seguridad](../how-to-make-a-type-safe-collection.md)de tipos .

### <a name="requirements"></a>Requisitos

  **Encabezado** afxtempl.h

## <a name="see-also"></a>Consulte también

[Macros y variables globales](mfc-macros-and-globals.md)<br/>
[Clase CMap](cmap-class.md)<br/>
[Clase CList](clist-class.md)<br/>
[CArray (clase)](carray-class.md)
