---
title: Clase CSize
ms.date: 10/18/2018
f1_keywords:
- CSize
- ATLTYPES/ATL::CSize
- ATLTYPES/ATL::CSize::CSize
helpviewer_keywords:
- SIZE
- dimensions, MFC
- dimensions
- CSize class
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
ms.openlocfilehash: dc876781cca568a332072938bec2cda0afb2ac8b
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746972"
---
# <a name="csize-class"></a>Clase CSize

Similar a la estructura [SIZE](/windows/win32/api/windef/ns-windef-size) de Windows, que implementa una coordenada relativa o una posición.

## <a name="syntax"></a>Sintaxis

```
class CSize : public tagSIZE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSize::CSize](#csize)|Construye un objeto `CSize`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CSize::operador -](#operator_-)|Resta dos tamaños.|
|[CSize::operador !-](#operator_neq)|Comprueba la desigualdad `CSize` entre un tamaño y un tamaño.|
|[CSize::operador +](#operator_add)|Añade dos tamaños.|
|[CSize::operador +](#operator_add_eq)|Agrega un tamaño `CSize`a .|
|[CSize::operador --](#operator_-_eq)|Resta un `CSize`tamaño de .|
|[CSize::operador ?](#operator_eq_eq)|Comprueba la igualdad `CSize` entre un tamaño y un tamaño.|

## <a name="remarks"></a>Observaciones

Esta clase se deriva `SIZE` de la estructura. Esto significa que `CSize` puede pasar un parámetro `SIZE` que llama a `SIZE` y que los `CSize`miembros de datos de la estructura son miembros de datos accesibles de .

Los `cx` `cy` miembros `SIZE` y `CSize`miembros de (y ) son públicos. Además, `CSize` implementa funciones `SIZE` miembro para manipular la estructura.

> [!NOTE]
> Para obtener más información sobre `CSize`las clases de utilidad compartidas (como ), vea [Clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes.h

## <a name="csizecsize"></a><a name="csize"></a>CSize::CSize

Construye un objeto `CSize`.

```
CSize() throw();
CSize( int initCX, int initCY) throw();
CSize( SIZE initSize) throw();
CSize( POINT initPt) throw();
CSize( DWORD dwSize) throw();
```

### <a name="parameters"></a>Parámetros

*initCX*<br/>
Establece `cx` el miembro `CSize`para el archivo .

*initCY*<br/>
Establece `cy` el miembro `CSize`para el archivo .

*initSize*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size) estructura `CSize` u objeto `CSize`utilizado para inicializar .

*initPt*<br/>
[ESTRUCTURA](/windows/win32/api/windef/ns-windef-point) POINT `CPoint` u objeto `CSize`utilizado para inicializar .

*dwSize*<br/>
DWORD utilizado `CSize`para inicializar . La palabra de orden `cx` bajo es el miembro `cy` y la palabra de orden superior es el miembro.

### <a name="remarks"></a>Observaciones

Si no se proporciona `cx` `cy` ningún argumento y se inicializan en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

## <a name="csizeoperator-"></a><a name="operator_eq_eq"></a>CSize::operador ?

Comprueba la igualdad entre dos tamaños.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve distinto de cero si los tamaños son iguales, otherwize 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

## <a name="csizeoperator-"></a><a name="operator_neq"></a>CSize::operador !-

Comprueba la desigualdad entre dos tamaños.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Observaciones

Devuelve distinto de cero si los tamaños no son iguales, en caso contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add_eq"></a>CSize::operador +

Agrega un tamaño `CSize`a este archivo .

```cpp
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-_eq"></a>CSize::operador --

Resta un tamaño `CSize`de este archivo .

```cpp
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

## <a name="csizeoperator-"></a><a name="operator_add"></a>CSize::operador +

Estos operadores `CSize` agregan este valor al valor de parameter.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Observaciones

Consulte las siguientes descripciones de los operadores individuales:

- **operador +(** *tamaño* **)**

  Esta operación `CSize` agrega dos valores.

- **operador +(** *punto* **)**

  Esta operación desfasa (mueve) un `CSize` valor [POINT](/windows/win32/api/windef/ns-windef-point) (o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) por este valor. Los `cx` `cy` miembros `CSize` y de este `x` `y` valor se `POINT` agregan a los miembros y datos del valor. Es análogo a la versión de [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) que toma un parámetro [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operador +(** *lpRect* **)**

   Esta operación desfasa (mueve) un valor `CSize` [RECT](/windows/win32/api/windef/ns-windef-rect) (o [CRect](../../atl-mfc-shared/reference/crect-class.md)) por este valor. Los `cx` `cy` miembros `CSize` y miembros `left`de `top` `right`este `bottom` valor se `RECT` agregan a los miembros , , y data del valor. Es análogo a la versión de [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) que toma un parámetro [SIZE.](/windows/win32/api/windef/ns-windef-size)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

## <a name="csizeoperator--"></a><a name="operator_-"></a>CSize::operador -

Los tres primeros de `CSize` estos operadores restan este valor al valor del parámetro.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Observaciones

El cuarto operador, el menos unario, `CSize` cambia el signo del valor. Consulte las siguientes descripciones de los operadores individuales:

- **operador -(** *tamaño* **)**

  Esta operación `CSize` resta dos valores.

- **operador -(** *punto* **)**

  Esta operación compensa (mueve) [un](/windows/win32/api/windef/ns-windef-point) POINT o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) `CSize` valor por el aditivo inverso de este valor. El `cx` `cy` y `CSize` de este valor `x` se `y` restan `POINT` de los miembros de datos y del valor. Es análogo a la versión de [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) que toma un parámetro [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operador -(** *lpRect* **)**

  Esta operación compensa (mueve) un valor [RECT](/windows/win32/api/windef/ns-windef-rect) o [CRect](../../atl-mfc-shared/reference/crect-class.md) por el aditivo inverso de este `CSize` valor. Los `cx` `cy` miembros `CSize` y de este `left`valor `top` `right`se `bottom` restan de `RECT` los miembros , , y los datos del valor. Es análogo a la versión de [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) que toma un parámetro [SIZE.](/windows/win32/api/windef/ns-windef-size)

- **operador -()**

  Esta operación devuelve el `CSize` aditivo inverso de este valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CRect](../../atl-mfc-shared/reference/crect-class.md)<br/>
[Clase CPoint](../../atl-mfc-shared/reference/cpoint-class.md)
