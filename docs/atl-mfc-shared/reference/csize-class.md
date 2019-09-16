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
ms.openlocfilehash: 26bb43355f4dff3f77a905068bea83dd1ceaf79c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491655"
---
# <a name="csize-class"></a>Clase CSize

Similar a la estructura [SIZE](/windows/win32/api/windef/ns-windef-size) de Windows, que implementa una coordenada relativa o una posición.

## <a name="syntax"></a>Sintaxis

```
class CSize : public tagSIZE
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSize::CSize](#csize)|Construye un objeto `CSize`.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CSize:: Operator-](#operator_-)|Resta dos tamaños.|
|[CSize:: Operator! =](#operator_neq)|Comprueba la desigualdad entre `CSize` y un tamaño.|
|[CSize:: Operator +](#operator_add)|Agrega dos tamaños.|
|[CSize:: Operator + =](#operator_add_eq)|Agrega un tamaño a `CSize`.|
|[CSize:: Operator-=](#operator_-_eq)|Resta un tamaño de `CSize`.|
|[CSize::operator ==](#operator_eq_eq)|Comprueba la igualdad entre `CSize` y un tamaño.|

## <a name="remarks"></a>Comentarios

Esta clase se deriva de la `SIZE` estructura. Esto significa que puede pasar un `CSize` en un parámetro que llama a para `SIZE` un y que los miembros de datos `SIZE` de la estructura son miembros de `CSize`datos accesibles de.

Los `cx` miembros `cy` y de `SIZE` ( y`CSize`) son públicos. Además, `CSize` implementa las funciones miembro para manipular la `SIZE` estructura.

> [!NOTE]
> Para obtener más información sobre las clases de utilidad `CSize`compartidas (como), vea [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagSIZE`

`CSize`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes. h

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
Establece el `cx` miembro `CSize`para.

*initCY*<br/>
Establece el `cy` miembro `CSize`para.

*initSize*<br/>
Estructura [SIZE](/windows/win32/api/windef/ns-windef-size) u objeto `CSize` que se usa para inicializar `CSize`.

*initPt*<br/>
Estructura [POINT](/windows/win32/api/windef/ns-windef-point) u objeto `CPoint` que se usa para inicializar `CSize`.

*dwSize*<br/>
DWORD que se usa `CSize`para inicializar. La palabra de orden inferior es el `cx` miembro y la palabra de orden superior es el `cy` miembro.

### <a name="remarks"></a>Comentarios

Si no se proporciona ningún argumento `cx` , `cy` y se inicializan en cero.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#97](../../atl-mfc-shared/codesnippet/cpp/csize-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CSize:: Operator = =

Comprueba la igualdad entre dos tamaños.

```
BOOL operator==(SIZE size) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve un valor distinto de cero si los tamaños son iguales, otherwize 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#98](../../atl-mfc-shared/codesnippet/cpp/csize-class_2.cpp)]

##  <a name="operator_neq"></a>CSize:: Operator! =

Comprueba la desigualdad entre dos tamaños.

```
BOOL operator!=(SIZE size) const throw();
```

### <a name="remarks"></a>Comentarios

Devuelve un valor distinto de cero si los tamaños no son iguales; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#99](../../atl-mfc-shared/codesnippet/cpp/csize-class_3.cpp)]

##  <a name="operator_add_eq"></a>CSize:: Operator + =

Agrega un tamaño a este `CSize`.

```
void operator+=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#100](../../atl-mfc-shared/codesnippet/cpp/csize-class_4.cpp)]

##  <a name="operator_-_eq"></a>CSize:: Operator-=

Resta un tamaño de este `CSize`.

```
void operator-=(SIZE size) throw();
```

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#101](../../atl-mfc-shared/codesnippet/cpp/csize-class_5.cpp)]

##  <a name="operator_add"></a>CSize:: Operator +

Estos operadores agregan `CSize` este valor al valor del parámetro.

```
CSize operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="remarks"></a>Comentarios

Vea las siguientes descripciones de los operadores individuales:

- **operador + (** *tamaño* **)**

  Esta operación agrega dos `CSize` valores.

- **operador + (** *punto* **)**

  Esta operación desplazará (mueve) un valor de [punto](/previous-versions/dd162805\(v=vs.85\)) (o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)) `CSize` por este valor. Los `cx` miembros `cy` y de este `CSize` valor se `x` agregan`y` a los miembros de datos y del valor.`POINT` Es análogo a la versión de [CPoint:: Operator +](../../atl-mfc-shared/reference/cpoint-class.md#operator_add) que toma un parámetro de [tamaño](/windows/win32/api/windef/ns-windef-size) .

- **operador + (** *lpRect* **)**

   Esta operación desplazará (mueve) un valor [Rect](/previous-versions/dd162897\(v=vs.85\)) (o [CRect](../../atl-mfc-shared/reference/crect-class.md)) por `CSize` este valor. Los `cx` miembros `cy` y de este `CSize` valor se agregan a `left`los `top`miembros de datos `bottom` ,, `right`y del `RECT` valor. Es análogo a la versión de [CRect:: Operator +](../../atl-mfc-shared/reference/crect-class.md#operator_add) que toma un parámetro de [tamaño](/windows/win32/api/windef/ns-windef-size) .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#102](../../atl-mfc-shared/codesnippet/cpp/csize-class_6.cpp)]

##  <a name="operator_-"></a>CSize:: Operator-

Los tres primeros operadores restan este `CSize` valor al valor del parámetro.

```
CSize operator-(SIZE size) const throw();
CPoint operator-(POINT point) const throw();
CRect operator-(const RECT* lpRect) const throw();
CSize operator-() const throw();
```

### <a name="remarks"></a>Comentarios

El cuarto operador, el unario menos, cambia el signo del `CSize` valor. Vea las siguientes descripciones de los operadores individuales:

- **operador-(** *tamaño* **)**

  Esta operación resta dos `CSize` valores.

- **operador-(** *punto* **)**

  Esta operación desplaza (mueve) un valor de [punto](/previous-versions/dd162805\(v=vs.85\)) o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) por el inverso aditivo de este `CSize` valor. `y` `x` Y de este valor`CSize` se restan de los miembros de datos y del `POINT` valor. `cy` `cx` Es análogo a la versión de [CPoint:: Operator,](../../atl-mfc-shared/reference/cpoint-class.md#operator_-) que toma un parámetro de [tamaño](/windows/win32/api/windef/ns-windef-size) .

- **operador-(** *lpRect* **)**

  Esta operación desplazará (mueve) un valor [Rect](/previous-versions/dd162897\(v=vs.85\)) o [CRect](../../atl-mfc-shared/reference/crect-class.md) por el inverso aditivo de este `CSize` valor. Los `cx` miembros `cy` y de este `CSize` valor se restan de los `left`miembros de `top`datos `right`,, `bottom` y del `RECT` valor. Es análogo a la versión de [CRect:: Operator,](../../atl-mfc-shared/reference/crect-class.md#operator_-) que toma un parámetro de [tamaño](/windows/win32/api/windef/ns-windef-size) .

- **operator -()**

  Esta operación devuelve el inverso aditivo de este `CSize` valor.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#103](../../atl-mfc-shared/codesnippet/cpp/csize-class_7.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CPoint (clase)](../../atl-mfc-shared/reference/cpoint-class.md)
