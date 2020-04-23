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
ms.openlocfilehash: 410f0101fd0f8cda271fe0f2353b06b9e8d773b8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754367"
---
# <a name="ctypedptrmap-class"></a>Clase CTypedPtrMap

Proporciona un "contenedor" con seguridad de tipos para objetos de las clases de asignación de puntero `CMapPtrToPtr`, `CMapPtrToWord`, `CMapWordToPtr`y `CMapStringToPtr`.

## <a name="syntax"></a>Sintaxis

```
template<class BASE_CLASS, class KEY, class VALUE>
class CTypedPtrMap : public BASE_CLASS
```

#### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Clase base de la clase de mapa de puntero con tipo; debe ser una clase `CMapPtrToPtr` `CMapPtrToWord`de `CMapWordToPtr`mapa `CMapStringToPtr`de puntero ( , , , o ).

*Clave*<br/>
Clase del objeto utilizado como clave del mapa.

*Valor*<br/>
Clase del objeto almacenado en el mapa.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTypedPtrMap::GetNextAssoc](#getnextassoc)|Obtiene el siguiente elemento para iterar.|
|[CTypedPtrMap::Lookup](#lookup)|Devuelve `KEY` un archivo `VALUE`basado en un archivo .|
|[CTypedPtrMap::RemoveKey](#removekey)|Quita un elemento especificado por una clave.|
|[CTypedPtrMap::SetAt](#setat)|Inserta un elemento en el mapa; reemplaza un elemento existente si se encuentra una clave coincidente.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CTypedPtrMap::operator \[\]](#operator_at)|Inserta un elemento en el mapa.|

## <a name="remarks"></a>Observaciones

Cuando se `CTypedPtrMap`utiliza , la función de comprobación de tipos C++ ayuda a eliminar los errores causados por tipos de puntero no coincidentes.

Dado `CTypedPtrMap` que todas las funciones están en línea, el uso de esta plantilla no afecta significativamente al tamaño o la velocidad del código.

Para obtener más `CTypedPtrMap`información sobre el uso de , vea los artículos [Colecciones](../../mfc/collections.md) y [Clases basadas en plantillas](../../mfc/template-based-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`BASE_CLASS`

`CTypedPtrMap`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxtempl.h

## <a name="ctypedptrmapgetnextassoc"></a><a name="getnextassoc"></a>CTypedPtrMap::GetNextAssoc

Recupera el elemento `rNextPosition`de mapa `rNextPosition` en , a continuación, se actualiza para hacer referencia al siguiente elemento del mapa.

```cpp
void GetNextAssoc(
    POSITION& rPosition,
    KEY& rKey,
    VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*rPosición*<br/>
Especifica una referencia a un position `GetNextAssoc` valor `BASE_CLASS`devuelto por una llamada anterior o **::GetStartPosition.**

*Clave*<br/>
Parámetro de plantilla que especifica el tipo de claves del mapa.

*rKey*<br/>
Especifica la clave devuelta del elemento recuperado.

*Valor*<br/>
Parámetro de plantilla que especifica el tipo de los valores del mapa.

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado.

### <a name="remarks"></a>Observaciones

Esta función es más útil para recorrer en iteración todos los elementos del mapa. Tenga en cuenta que la secuencia de posición no es necesariamente la misma que la secuencia de valores de clave.

Si el elemento recuperado es el último del mapa, el nuevo valor de `rNextPosition` se establece en NULL.

Esta función `BASE_CLASS`en línea llama **a ::GetNextAssoc**.

## <a name="ctypedptrmaplookup"></a><a name="lookup"></a>CTypedPtrMap::Lookup

`Lookup`utiliza un algoritmo hash para encontrar rápidamente el elemento de mapa con una clave que coincida exactamente.

```
BOOL Lookup(BASE_CLASS ::BASE_ARG_KEY key, VALUE& rValue) const;
```

### <a name="parameters"></a>Parámetros

*BASE_CLASS*<br/>
Parámetro de plantilla que especifica la clase base de la clase de este mapa.

*key*<br/>
La clave del elemento que se va a buscar.

*Valor*<br/>
Parámetro de plantilla que especifica el tipo de valores almacenados en este mapa.

*rValue*<br/>
Especifica el valor devuelto del elemento recuperado.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si se encontró el elemento; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Esta función `BASE_CLASS`en línea llama **::Lookup**.

## <a name="ctypedptrmapoperator--"></a><a name="operator_at"></a>CTypedPtrMap::operator [ ]

Este operador solo se puede utilizar en el lado izquierdo de una instrucción de asignación (un valor l).

```
VALUE& operator[ ](base_class ::base_arg_key key);
```

### <a name="parameters"></a>Parámetros

*Valor*<br/>
Parámetro de plantilla que especifica el tipo de valores almacenados en este mapa.

*BASE_CLASS*<br/>
Parámetro de plantilla que especifica la clase base de la clase de este mapa.

*key*<br/>
La clave del elemento que se va a buscar o crear en el mapa.

### <a name="remarks"></a>Observaciones

Si no hay ningún elemento de mapa con la clave especificada, se crea un nuevo elemento. No hay ningún "lado derecho" (valor r) equivalente a este operador porque existe la posibilidad de que no se encuentre una clave en el mapa. Utilice `Lookup` la función miembro para la recuperación de elementos.

## <a name="ctypedptrmapremovekey"></a><a name="removekey"></a>CTypedPtrMap::RemoveKey

Esta función `BASE_CLASS`miembro llama **a ::RemoveKey**.

```
BOOL RemoveKey(KEY key);
```

### <a name="parameters"></a>Parámetros

*Clave*<br/>
Parámetro de plantilla que especifica el tipo de claves del mapa.

*key*<br/>
Clave para el elemento que se va a quitar.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la entrada se encontró y se quitó correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CMapStringToOb::RemoveKey](../../mfc/reference/cmapstringtoob-class.md#removekey).

## <a name="ctypedptrmapsetat"></a><a name="setat"></a>CTypedPtrMap::SetAt

Esta función `BASE_CLASS`miembro llama **a ::SetAt**.

```cpp
void SetAt(KEY key, VALUE newValue);
```

### <a name="parameters"></a>Parámetros

*Clave*<br/>
Parámetro de plantilla que especifica el tipo de claves del mapa.

*key*<br/>
Especifica el valor de clave de newValue.

*newValue*<br/>
Especifica el puntero de objeto que es el valor del nuevo elemento.

### <a name="remarks"></a>Observaciones

Para obtener comentarios más detallados, vea [CMapStringToOb::SetAt](../../mfc/reference/cmapstringtoob-class.md#setat).

## <a name="see-also"></a>Vea también

[RECOPILACIÓN de muestras de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CMapPtrToPtr (clase)](../../mfc/reference/cmapptrtoptr-class.md)<br/>
[Clase CMapPtrToWord](../../mfc/reference/cmapptrtoword-class.md)<br/>
[Clase CMapWordToPtr](../../mfc/reference/cmapwordtoptr-class.md)<br/>
[Clase CMapStringToPtr](../../mfc/reference/cmapstringtoptr-class.md)
