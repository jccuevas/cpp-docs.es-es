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
ms.openlocfilehash: 331b89ff118f727303e887670960ee6078b01fb1
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747085"
---
# <a name="cpoint-class"></a>Clase CPoint

Similar a la estructura `POINT` de Windows.

## <a name="syntax"></a>Sintaxis

```
class CPoint : public tagPOINT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPoint::CPoint](#cpoint)|Construye un objeto `CPoint`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPoint::Offset](#offset)|Agrega valores a `x` `y` los miembros y miembros del `CPoint`archivo .|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPoint::operador -](#operator_-)|Devuelve la diferencia `CPoint` de a y un tamaño, o la negación de un punto, o la diferencia de tamaño entre dos puntos, o el desplazamiento por un tamaño negativo.|
|[CPoint::operador !-](#operator_neq)|Comprueba la desigualdad entre dos puntos.|
|[CPoint::operador +](#operator_add)|Devuelve la suma `CPoint` de a y un `CRect` tamaño o punto, o un desplazamiento por un tamaño.|
|[CPoint::operador +](#operator_add_eq)|Desplazamientos `CPoint` mediante la adición de un tamaño o un punto.|
|[CPoint::operador --](#operator_-_eq)|Desfases `CPoint` restando un tamaño o punto.|
|[CPoint::operador ?](#operator_eq_eq)|Comprueba la igualdad entre dos puntos.|

## <a name="remarks"></a>Observaciones

También incluye funciones `CPoint` miembro para manipular y [estructuras POINT.](/windows/win32/api/windef/ns-windef-point)

Un `CPoint` objeto se puede `POINT` utilizar siempre que se utilice una estructura. Los operadores de esta clase que interactúan con un "tamaño" aceptan [CSize](../../atl-mfc-shared/reference/csize-class.md) objetos o [SIZE](/windows/win32/api/windef/ns-windef-size) estructuras, ya que los dos son intercambiables.

> [!NOTE]
> Esta clase se deriva `tagPOINT` de la estructura. (El `tagPOINT` nombre es un nombre menos `POINT` comúnmente utilizado para la estructura.) Esto significa que los `POINT` miembros `x` `y`de datos de `CPoint`la estructura y , son miembros de datos accesibles de .

> [!NOTE]
> Para obtener más información sobre `CPoint`las clases de utilidad compartidas (como ), vea [Clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagPOINT`

`CPoint`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes.h

## <a name="cpointcpoint"></a><a name="cpoint"></a>CPoint::CPoint

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

*inidad*<br/>
Especifique el valor del miembro `y` de `CPoint`.

*initPt*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point) o `CPoint` que especifica los valores `CPoint`utilizados para inicializar .

*initSize*<br/>
[SIZE](/windows/win32/api/windef/ns-windef-size) o [CSize](../../atl-mfc-shared/reference/csize-class.md) que especifica los `CPoint`valores utilizados para inicializar .

*dwPoint*<br/>
Establece `x` el miembro en la palabra de `y` orden bajo de *dwPoint* y el miembro en la palabra de orden superior de *dwPoint*.

### <a name="remarks"></a>Observaciones

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

## <a name="cpointoffset"></a><a name="offset"></a>CPoint::Offset

Agrega valores a `x` `y` los miembros y miembros del `CPoint`archivo .

```cpp
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>Parámetros

*xOffset*<br/>
Especifica la cantidad que `x` se `CPoint`va a desfasar el miembro del archivo .

*yOffset*<br/>
Especifica la cantidad que `y` se `CPoint`va a desfasar el miembro del archivo .

*Punto*<br/>
Especifica el importe [POINT](/windows/win32/api/windef/ns-windef-point) ( `CPoint`POINT o `CPoint`) para desfasar el archivo .

*size*<br/>
Especifica la cantidad ( [SIZE](/windows/win32/api/windef/ns-windef-size) o [CSize](../../atl-mfc-shared/reference/csize-class.md)) para compensar el `CPoint`archivo .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

## <a name="cpointoperator-"></a><a name="operator_eq_eq"></a>CPoint::operador ?

Comprueba la igualdad entre dos puntos.

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Contiene [POINT](/windows/win32/api/windef/ns-windef-point) un POINT `CPoint` estructura u objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los puntos son iguales; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

## <a name="cpointoperator-"></a><a name="operator_neq"></a>CPoint::operador !-

Comprueba la desigualdad entre dos puntos.

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Contiene [POINT](/windows/win32/api/windef/ns-windef-point) un POINT `CPoint` estructura u objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los puntos no son iguales; de lo contrario 0.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add_eq"></a>CPoint::operador +

La primera sobrecarga agrega un `CPoint`tamaño al archivo .

```cpp
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punto*<br/>
Contiene un [POINT](/windows/win32/api/windef/ns-windef-point) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.

### <a name="remarks"></a>Observaciones

La segunda sobrecarga agrega un `CPoint`punto al archivo .

En ambos casos, la adición `x` `cx`se realiza agregando el miembro `x` (o `CPoint` ) `y` del `cy`operando derecho al miembro del `y` miembro y `CPoint`agregando el miembro (o ) del operando derecho al miembro del archivo .

Por ejemplo, `CPoint(5, -7)` agregar a `CPoint(30, 40)` una variable `CPoint(35, 33)`que contiene cambia la variable a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-_eq"></a>CPoint::operador --

La primera sobrecarga resta `CPoint`un tamaño del archivo .

```cpp
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punto*<br/>
Contiene un [POINT](/windows/win32/api/windef/ns-windef-point) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.

### <a name="remarks"></a>Observaciones

La segunda sobrecarga resta `CPoint`un punto del archivo .

En ambos casos, la resta `x` se `cx`realiza restando el miembro `x` (o `CPoint` ) del `y` operando `cy`derecho del miembro y restando el miembro (o ) del operando derecho del `y` miembro del `CPoint`archivo .

Por ejemplo, `CPoint(5, -7)` restar de `CPoint(30, 40)` una variable `CPoint(25, 47)`que contiene cambia la variable a .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

## <a name="cpointoperator-"></a><a name="operator_add"></a>CPoint::operador +

Utilice este operador `CPoint` para `CPoint` `CSize` desplazarse por un `CRect` objeto `CPoint`o, o para desplazar a por un archivo .

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Contiene una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize.](../../atl-mfc-shared/reference/csize-class.md)

*Punto*<br/>
Contiene un [POINT](/windows/win32/api/windef/ns-windef-point) estructura o [CPoint](../../atl-mfc-shared/reference/cpoint-class.md) objeto.

*lpRect*<br/>
Contiene un puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) o [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

A `CPoint` que se desfasa por un tamaño, un `CPoint` que se desfasa por un punto o un `CRect` desplazamiento por un punto.

### <a name="remarks"></a>Observaciones

Por ejemplo, el uso de una de `CPoint(25, -19)` las dos `CPoint(15, 5)` primeras sobrecargas para desplazar el punto por un punto o tamaño `CSize(15, 5)` devuelve el valor `CPoint(40, -14)`.

Agregar un rectángulo a un punto devuelve `x` el `y` rectángulo después de ser desfase por los valores especificados en el punto. Por ejemplo, al utilizar la `CRect(125, 219, 325, 419)` última sobrecarga `CPoint(25, -19)` `CRect(150, 200, 350, 400)`para desplazar un rectángulo por un punto devuelve .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

## <a name="cpointoperator--"></a><a name="operator_-"></a>CPoint::operador -

Utilice una de las dos primeras sobrecargas para restar un `CPoint` objeto u `CSize` objeto de `CPoint`.

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint.](../../atl-mfc-shared/reference/cpoint-class.md)

*size*<br/>
Una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o [cSize](../../atl-mfc-shared/reference/csize-class.md) objeto.

*lpRect*<br/>
Puntero a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) o a un objeto [CRect.](../../atl-mfc-shared/reference/crect-class.md)

### <a name="return-value"></a>Valor devuelto

A `CSize` que es la diferencia `CPoint` entre dos puntos, a que `CRect` se compensa por la negación de `CPoint` un tamaño, a que se compensa por la negación de un punto, o a que es la negación de un punto.

### <a name="remarks"></a>Observaciones

La tercera sobrecarga `CRect` compensa a por `CPoint`la negación de . Por último, utilice el operador `CPoint`unario para negar .

Por ejemplo, utilizando la primera sobrecarga `CPoint(25, -19)` para `CPoint(15, 5)` `CSize(10, -24)`encontrar la diferencia entre dos puntos y devuelve .

Restar `CSize` un `CPoint` de hace el mismo `CPoint` cálculo que `CSize` el anterior, pero devuelve un objeto, no un objeto. Por ejemplo, el uso de la segunda `CPoint(25, -19)` sobrecarga `CSize(15, 5)` para `CPoint(10, -24)`encontrar la diferencia entre el punto y el tamaño devuelve .

Al restar un rectángulo de un punto, se `x` `y` devuelve el desplazamiento del rectángulo por los negativos de los valores especificados en el punto. Por ejemplo, el uso de `CRect(125, 200, 325, 400)` la última `CPoint(25, -19)` `CRect(100, 219, 300, 419)`sobrecarga para desplazar el rectángulo por el punto devuelve .

Utilice el operador unario para negar un punto. Por ejemplo, el uso del `CPoint(25, -19)` operador `CPoint(-25, 19)`unario con el punto devuelve .

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Estructura POINT](/windows/win32/api/windef/ns-windef-point)<br/>
[Clase CRect](../../atl-mfc-shared/reference/crect-class.md)<br/>
[Clase CSize](../../atl-mfc-shared/reference/csize-class.md)
