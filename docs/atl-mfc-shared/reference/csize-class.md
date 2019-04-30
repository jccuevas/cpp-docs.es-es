---
title: CSize (clase)
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
ms.openlocfilehash: 5e19ab9b9339f3e6f61abf7731a40ed3832b50c9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252693"
---
# <a name="csize-class"></a>CSize (clase)

Similar a la estructura [SIZE](/windows/desktop/api/windef/ns-windef-tagsize) de Windows, que implementa una coordenada relativa o una posición.

## <a name="syntax"></a>Sintaxis

```
class CSize : public tagSIZE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CSize::CSize](#csize)|Construye un objeto `CSize`.|

### <a name="public-operators"></a>Operadores públicos

|Name|Descripción|
|----------|-----------------|
|[CSize::operator -](#operator_-)|Resta dos tamaños.|
|[CSize::operator !=](#operator_neq)|Comprueba la desigualdad entre `CSize` y un tamaño.|
|[CSize::operator +](#operator_add)|Agrega dos tamaños.|
|[CSize::operator +=](#operator_add_eq)|Agrega un tamaño para `CSize`.|
|[CSize::operator -=](#operator_-_eq)|Resta un tamaño de `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Comprueba la igualdad entre `CSize` y un tamaño.|

## <a name="remarks"></a>Comentarios

Esta clase se deriva el `SIZE` estructura. Esto significa que puede pasar un `CSize` en un parámetro que requiere un `SIZE` y que los miembros de datos de la `SIZE` estructura son miembros de datos accesibles de `CSize`.

El `cx` y `cy` los miembros de `SIZE` (y `CSize`) son públicos. Además, `CSize` implementa las funciones miembro para manipular el `SIZE` estructura.

> [!NOTE]
> Para obtener más información sobre las clases de utilidad de compartido (como `CSize`), consulte [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes.h

##  <a name="csize"></a>  CSize::CSize

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
Establece el `cx` miembro para el `CSize`.

*initCY*<br/>
Establece el `cy` miembro para el `CSize`.

*initSize*<br/>
[TAMAÑO](/windows/desktop/api/windef/ns-windef-tagsize) estructura o `CSize` objeto usado para inicializar `CSize`.

*initPt*<br/>
[PUNTO](/windows/desktop/api/windef/ns-windef-tagpoint) estructura o `CPoint` objeto usado para inicializar `CSize`.

*dwSize*<br/>
DWORD que se usa para inicializar `CSize`. La palabra de orden inferior es la `cx` miembro y la palabra de orden superior es el `cy` miembro.

### <a name="remarks"></a>Comentarios

Si no se proporcionan argumentos, `cx` y `cy` se inicializan en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>  CSize::operator ==

Comprueba la igualdad entre dos tamaños.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve cero si los tamaños son iguales, otherwize 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>  CSize::operator! =

Comprueba la desigualdad entre dos tamaños.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve cero si los tamaños no son iguales; en caso contrario, 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>  CSize::operator +=

Agrega un tamaño a este `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>  CSize::operator =

Resta un tamaño de este `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>  CSize::operator +

Estos operadores agregar esto `CSize` valor para el valor del parámetro.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Comentarios

Consulte las siguientes descripciones de los operadores individuales:

- **operador + (** *tamaño* **)**

  Esta operación agrega dos `CSize` valores.

- **operador + (** *punto* **)**

  Esta operación desplazamientos (mueve) un [punto](/previous-versions/dd162805\(v=vs.85\)) (o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) valor vieron `CSize` valor. El `cx` y `cy` los miembros de este `CSize` se agregan valor a la `x` y `y` miembros de datos de la `POINT` valor. De forma análoga a la versión de [CPoint::operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) que toma un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) parámetro.

- **operador + (** *lpRect* **)**

   Esta operación desplazamientos (mueve) un [RECT](/previous-versions/dd162897\(v=vs.85\)) (o [CRect](../../atl-mfc-shared/reference/crect-class.md)) valor vieron `CSize` valor. El `cx` y `cy` los miembros de este `CSize` se agregan valor a la `left`, `top`, `right`, y `bottom` miembros de datos de la `RECT` valor. De forma análoga a la versión de [CRect::operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) que toma un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) parámetro.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>  CSize::operator -

Los primeros tres de estos operadores restar esto `CSize` valor para el valor del parámetro.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Comentarios

El cuarto operador, el unario menos, cambia el signo de la `CSize` valor. Consulte las siguientes descripciones de los operadores individuales:

- **operator -(** *size* **)**

  Esta operación de resta dos `CSize` valores.

- **operator -(** *point* **)**

  Esta operación desplazamientos (mueve) un [punto](/previous-versions/dd162805\(v=vs.85\)) o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) valor por el inverso aditivo de este `CSize` valor. El `cx` y `cy` esto `CSize` se restan valor a la `x` y `y` miembros de datos de la `POINT` valor. De forma análoga a la versión de [CPoint::operator -](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) que toma un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) parámetro.

- **operator -(** *lpRect* **)**

  Esta operación desplazamientos (mueve) un [RECT](/previous-versions/dd162897\(v=vs.85\)) o [CRect](../../atl-mfc-shared/reference/crect-class.md) valor por el inverso aditivo de este `CSize` valor. El `cx` y `cy` los miembros de este `CSize` se restan valor a la `left`, `top`, `right`, y `bottom` miembros de datos de la `RECT` valor. De forma análoga a la versión de [CRect::operator -](../../atl-mfc-shared/reference/crect-class.md#operator_-) que toma un [tamaño](/windows/desktop/api/windef/ns-windef-tagsize) parámetro.

- **operator -()**

  Esta operación devuelve el inverso aditivo de este `CSize` valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint (clase)](../../atl-mfc-shared/reference/cpoint-class.md)
