---
title: Clase CPoint
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491221"
---
# <a name="cpoint-class"></a>Clase CPoint

Similar a la estructura `POINT` de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Construye un objeto `CPoint`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPoint::Offset](#offset)|Agrega valores a los `x` miembros `y` y de `CPoint`.|

### <a name="public-operators"></a>Operadores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPoint:: Operator-](#operator_-)|Devuelve la diferencia de un `CPoint` y un tamaño, o la negación de un punto, o la diferencia de tamaño entre dos puntos, o el desplazamiento por un tamaño negativo.|
|[CPoint:: Operator! =](#operator_neq)|Comprueba la desigualdad entre dos puntos.|
|[CPoint:: Operator +](#operator_add)|Devuelve la suma de un `CPoint` y un tamaño o punto, o un `CRect` desplazamiento por tamaño.|
|[CPoint:: Operator + =](#operator_add_eq)|`CPoint` Desplazamientos agregando un tamaño o un punto.|
|[CPoint:: Operator-=](#operator_-_eq)|`CPoint` Desplazamientos restando un tamaño o un punto.|
|[CPoint::operator ==](#operator_eq_eq)|Comprueba la igualdad entre dos puntos.|

## <a name="remarks"></a>Comentarios

También incluye funciones miembro para manipular `CPoint` y estructuras de [punto](/windows/win32/api/windef/ns-windef-point) .

Se `CPoint` puede utilizar un objeto dondequiera que `POINT` se utilice una estructura. Los operadores de esta clase que interactúan con un "tamaño" aceptan objetos [CSize](../../atl-mfc-shared/reference/csize-class.md) o estructuras de [tamaño](/windows/win32/api/windef/ns-windef-size) , ya que los dos son intercambiables.

> [!NOTE]
>  Esta clase se deriva de la `tagPOINT` estructura. (El nombre `tagPOINT` es un nombre que se usa con menos `POINT` frecuencia para la estructura). Esto significa que los miembros de datos de `POINT` la estructura `x` , `y`y, son miembros de datos `CPoint`accesibles de.

> [!NOTE]
>  Para obtener más información sobre las clases de utilidad `CPoint`compartidas (como), vea [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes. h

##  <a name="cpoint"></a>  CPoint::CPoint

Construye un objeto `CPoint`.

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>Parámetros

*initX*<br/>
Especifique el valor del miembro `x` de `CPoint`.

*inicialización*<br/>
Especifique el valor del miembro `y` de `CPoint`.

*initPt*<br/>
Estructura [Point](/windows/win32/api/windef/ns-windef-point) o `CPoint` que especifica los valores utilizados para inicializar `CPoint`.

*initSize*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica los valores utilizados para `CPoint`inicializar.

*dwPoint*<br/>
Establece el `x` miembro en la palabra de orden inferior de *dwPoint* y el `y` miembro en la palabra de orden superior de *dwPoint*.

### <a name="remarks"></a>Comentarios

Si no se proporcionan argumentos, los miembros `x` e `y` se establecen en 0.

### <a name="example"></a>Ejemplo

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

##  <a name="offset"></a>  CPoint::Offset

Agrega valores a los `x` miembros `y` y de `CPoint`.

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parámetros

*xOffset*<br/>
Especifica la cantidad que se va `x` a desplazar el miembro `CPoint`de.

*yOffset*<br/>
Especifica la cantidad que se va `y` a desplazar el miembro `CPoint`de.

*point*<br/>
Especifica la cantidad ( [punto](/windows/win32/api/windef/ns-windef-point) o `CPoint` `CPoint`) que se va a desplazar.

*size*<br/>
Especifica la cantidad ( [tamaño](/windows/win32/api/windef/ns-windef-size) o [CSize](../../atl-mfc-shared/reference/csize-class.md)) `CPoint`que se va a desplazar.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CPoint:: Operator = =

Comprueba la igualdad entre dos puntos.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Contiene una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto `CPoint`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los puntos son iguales; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint:: Operator! =

Comprueba la desigualdad entre dos puntos.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Contiene una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto `CPoint`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los puntos no son iguales; de lo contrario, es 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint:: Operator + =

La primera sobrecarga agrega un tamaño a `CPoint`.

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contiene una estructura de [punto](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Comentarios

La segunda sobrecarga agrega un punto a `CPoint`.

En ambos casos, la suma se realiza agregando `x` el miembro `cx`(o) del operando `CPoint` derecho al `x` miembro de y agregando el `y` miembro (o `cy`) del operando derecho al `y` miembro`CPoint`de.

Por ejemplo, agregar `CPoint(5, -7)` a una variable que contenga `CPoint(30, 40)` cambia la variable `CPoint(35, 33)`a.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint:: Operator-=

La primera sobrecarga resta un tamaño de `CPoint`.

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contiene una estructura de [punto](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

### <a name="remarks"></a>Comentarios

La segunda sobrecarga resta un punto de `CPoint`.

En ambos casos, la resta se realiza restando el `x` miembro (o `cx`) del operando `x` derecho del miembro de `CPoint` y restando el `y` miembro (o `cy`) del lado derecho. operando del `CPoint`miembro de. `y`

Por ejemplo, restar `CPoint(5, -7)` de una variable que contiene `CPoint(30, 40)` cambia la variable a `CPoint(25, 47)`.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint:: Operator +

Utilice este operador para desplazarse `CPoint` por `CSize` un `CPoint` objeto o, o para `CRect` desplazar un por un `CPoint`.

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*point*<br/>
Contiene una estructura de [punto](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*lpRect*<br/>
Contiene un puntero a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Valor devuelto

Que se desplaza por un tamaño `CPoint` , que es un desplazamiento por un punto o un `CRect` desplazamiento por un punto. `CPoint`

### <a name="remarks"></a>Comentarios

Por ejemplo, si se usa una de las dos primeras sobrecargas para desplazar el punto `CPoint(25, -19)` por `CSize(15, 5)` un punto `CPoint(15, 5)` o `CPoint(40, -14)`tamaño, se devuelve el valor.

Al agregar un rectángulo a un punto, se devuelve el rectángulo tras desplazarse por los `x` valores y `y` especificados en el punto. Por ejemplo, si se usa la última sobrecarga para desplazar un `CPoint(25, -19)` rectángulo `CRect(150, 200, 350, 400)` `CRect(125, 219, 325, 419)` por un punto, devuelve.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint:: Operator-

Use una de las dos primeras sobrecargas para restar `CPoint` un `CSize` objeto o `CPoint`de.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parámetros

*point*<br/>
Una estructura [Point](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) .

*size*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o objeto [CSize](../../atl-mfc-shared/reference/csize-class.md) .

*lpRect*<br/>
Puntero a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) .

### <a name="return-value"></a>Valor devuelto

Que es la diferencia entre dos puntos `CPoint` , que se desplaza por la negación de un tamaño, una `CRect` que se desplaza por la negación de un punto o un `CPoint` que es la negación de un punto. `CSize`

### <a name="remarks"></a>Comentarios

La tercera sobrecarga desplaza un `CRect` por la negación de. `CPoint` Por último, utilice el operador unario para `CPoint`negar.

Por ejemplo, si se usa la primera sobrecarga para encontrar la diferencia entre `CPoint(25, -19)` dos `CPoint(15, 5)` puntos `CSize(10, -24)`y devuelve.

Al restar un `CSize` de `CPoint` , se realiza el mismo cálculo que antes, `CPoint` pero se devuelve un `CSize` objeto, no un objeto. Por ejemplo, el uso de la segunda sobrecarga para encontrar la diferencia entre `CPoint(25, -19)` el punto y `CSize(15, 5)` el `CPoint(10, -24)`tamaño devuelto.

Al restar un rectángulo desde un punto, se devuelve el desplazamiento del rectángulo por los negativos `x` de `y` los valores y especificados en el punto. Por ejemplo, el uso de la última sobrecarga para desplazar el `CPoint(25, -19)` rectángulo `CRect(100, 219, 300, 419)` `CRect(125, 200, 325, 400)` por el punto devuelve.

Use el operador unario para negar un punto. Por ejemplo, si se usa el operador unario `CPoint(25, -19)` con `CPoint(-25, 19)`el punto, se devuelve.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[POINT (estructura)](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect (clase)](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize (clase)](../../atl-mfc-shared/reference/csize-class.md)
