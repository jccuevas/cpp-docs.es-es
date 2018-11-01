---
title: Clase CTypedPtrMap
ms.date: 11/04/2016
f1_keywords:
- CTypedPtrMap
- AFXTEMPL/CTypedPtrMap
- AFXTEMPL/CTypedPtrMap::GetNextAssoc
- AFXTEMPL/CTypedPtrMap::Lookup
- AFXTEMPL/CTypedPtrMap::RemoveKey
- AFXTEMPL/CTypedPtrMap::SetAt
helpviewer_keywords:
- CTypedPtrMap [MFC], GetNextAssoc
- CTypedPtrMap [MFC], Lookup
- CTypedPtrMap [MFC], RemoveKey
- CTypedPtrMap [MFC], SetAt
ms.assetid: 9f377385-c6e9-4471-8b40-8fe220c50164
ms.openlocfilehash: f09b44c5b898ee0d583db45ca63ee67c3d1c5b47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50494866"
---
# <a name="ctypedptrmap-class"></a>Clase CTypedPtrMap

Proporciona un "contenedor" con seguridad de tipos para objetos de las clases de asignación de puntero `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`y `CMapStringToPtr`.

## <a name="syntax"></a>Sintaxis

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parámetros

*$BASE_CLASS*<br/>
Clase base de la clase de mapa de puntero con tipo. debe ser una clase de mapa de puntero ( `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`, o `CMapStringToPtr`).

*KEY*<br/>
Clase del objeto se utiliza como clave para la asignación.

*VALOR*<br/>
Clase del objeto almacenado en el mapa.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtiene el elemento siguiente para efectuar una iteración.|
|[CTypedPtrMap::Lookup](#lookup)|Devuelve un `KEY` según un `VALUE`.|
|[CTypedPtrMap::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|
|[CTypedPtrMap::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[[] CTypedPtrMap::operator](#operator_at)|Inserta un elemento en el mapa.|

## <a name="remarks"></a>Comentarios

Cuando usas `CTypedPtrMap`, la utilidad de comprobación de tipos de C++ ayuda a eliminar errores causados por los tipos de puntero que no coinciden.

Dado que todos los `CTypedPtrMap` funciones están alineados, el uso de esta plantilla no afecta significativamente el tamaño o la velocidad del código.

Para obtener más información sobre el uso de `CTypedPtrMap`, consulte los artículos [colecciones](../../mfc/collections.md) y [clases basadas en plantillas](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

##  <a name="getnextassoc"></a>  CTypedPtrMap::GetNextAssoc

Recupera el elemento de mapa en `rNextPosition`, a continuación, actualiza `rNextPosition` para hacer referencia al elemento siguiente en el mapa.

```
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*rPosition*<br/>
Especifica una referencia a un valor de posición devuelto por un método `GetNextAssoc` o `BASE_CLASS` **:: GetStartPosition** llamar.

*KEY*<br/>
Parámetro de plantilla que especifica el tipo de las claves del mapa.

*rKey*<br/>
Especifica la clave devuelta del elemento recuperado.

*VALOR*<br/>
Parámetro de plantilla que especifica el tipo de valores del mapa.

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado.

### <a name="remarks"></a>Comentarios

Esta función es muy útil para recorrer en iteración todos los elementos en el mapa. Tenga en cuenta que la secuencia de posición no es necesariamente el mismo que la secuencia de valores de clave.

Si el elemento recuperado es el último en el mapa, a continuación, el nuevo valor de `rNextPosition` se establece en NULL.

Llama esta función inline `BASE_CLASS` **:: GetNextAssoc**.

##  <a name="lookup"></a>  CTypedPtrMap::Lookup

`Lookup` utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincide exactamente.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*$BASE_CLASS*<br/>
Parámetro de plantilla que especifica la clase base de la clase de este mapa.

*key*<br/>
La clave del elemento que se va a buscar.

*VALOR*<br/>
Parámetro de plantilla que especifica el tipo de los valores almacenados en este mapa.

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró el elemento; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Llama esta función inline `BASE_CLASS` **:: búsqueda**.

##  <a name="operator_at"></a>  [] CTypedPtrMap::operator

Este operador puede usarse solo en el lado izquierdo de una instrucción de asignación (un valor l).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parámetros

*VALOR*<br/>
Parámetro de plantilla que especifica el tipo de los valores almacenados en este mapa.

*$BASE_CLASS*<br/>
Parámetro de plantilla que especifica la clase base de la clase de este mapa.

*key*<br/>
La clave del elemento que se busca o crea en el mapa.

### <a name="remarks"></a>Comentarios

Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento. No hay ningún "derecha" (valor r) equivalente a este operador porque es posible que no se puede encontrar una clave en el mapa. Use el `Lookup` función miembro para la recuperación del elemento.

##  <a name="removekey"></a>  CTypedPtrMap::RemoveKey

Esta función miembro llama a `BASE_CLASS` **:: RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parámetros

*KEY*<br/>
Parámetro de plantilla que especifica el tipo de las claves del mapa.

*key*<br/>
Clave para que el elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró la entrada y se quita correctamente; en caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Para obtener comentarios más detallada, consulte [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

##  <a name="setat"></a>  CTypedPtrMap::SetAt

Esta función miembro llama a `BASE_CLASS` **:: SetAt**.

```
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parámetros

*KEY*<br/>
Parámetro de plantilla que especifica el tipo de las claves del mapa.

*key*<br/>
Especifica el valor de clave de la newValue.

*newValue*<br/>
Especifica el puntero de objeto que es el valor del nuevo elemento.

### <a name="remarks"></a>Comentarios

Para obtener comentarios más detallada, consulte [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Vea también

[Ejemplo de MFC COLLECT](../../visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr (clase)](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[CMapPtrToWord (clase)](../../mfc/reference/cmapptrtoword-class.md)<br/>
[CMapWordToPtr (clase)](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[CMapStringToPtr (clase)](../../mfc/reference/cmapstringtoptr-class.md)
