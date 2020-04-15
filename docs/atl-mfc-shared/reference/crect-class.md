---
title: Clase CRect
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: c59ed587e2c8e51f5c08a026a7ee0b9d0af25168
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317714"
---
# <a name="crect-class"></a>Clase CRect

Similar a una estructura [RECT de](/windows/win32/api/windef/ns-windef-rect) Windows.

## <a name="syntax"></a>Sintaxis

```
class CRect : public tagRECT
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect::CRect](#crect)|Construye un objeto `CRect`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect::BottomRight](#bottomright)|Devuelve el punto inferior `CRect`derecho de .|
|[CRect::CenterPoint](#centerpoint)|Devuelve el punto `CRect`central de .|
|[CRect::CopyRect](#copyrect)|Copia las dimensiones de `CRect`un rectángulo de origen en .|
|[CRect::DeflateRect](#deflaterect)|Disminuye la anchura y `CRect`la altura de .|
|[CRect::EqualRect](#equalrect)|Determina si `CRect` es igual al rectángulo especificado.|
|[CRect::Altura](#height)|Calcula la altura `CRect`de .|
|[CRect::InflateRect](#inflaterect)|Aumenta la anchura y `CRect`la altura de .|
|[CRect::IntersectRect](#intersectrect)|Establece `CRect` igual a la intersección de dos rectángulos.|
|[CRect::IsRectEmpty](#isrectempty)|Determina si `CRect` está vacío. `CRect`está vacío si el ancho y/o la altura son 0.|
|[CRect::IsRectNull](#isrectnull)|Determina si `top`las `bottom` `left`variables `right` , , y member son todas iguales a 0.|
|[CRect::MoveToX](#movetox)|Se `CRect` mueve a la coordenada x especificada.|
|[CRect::MoveToxY](#movetoxy)|Se `CRect` desplaza a las coordenadas x e y especificadas.|
|[CRect::MoveToY](#movetoy)|Se `CRect` mueve a la coordenada y especificada.|
|[CRect::NormalizeRect](#normalizerect)|Estandariza la altura y `CRect`la anchura de .|
|[CRect::OffsetRect](#offsetrect)|Se `CRect` mueve por los desplazamientos especificados.|
|[CRect::PtInRect](#ptinrect)|Determina si el punto especificado `CRect`se encuentra dentro de .|
|[CRect::SetRect](#setrect)|Establece las `CRect`dimensiones de .|
|[CRect::SetRectEmpty](#setrectempty)|Se `CRect` establece en un rectángulo vacío (todas las coordenadas iguales a 0).|
|[CRect::Tamaño](#size)|Calcula el tamaño `CRect`de .|
|[CRect::SubtractRect](#subtractrect)|Resta un rectángulo de otro.|
|[CRect::TopLeft](#topleft)|Devuelve el punto superior `CRect`izquierdo de .|
|[CRect::UnionRect](#unionrect)|Establece `CRect` igual a la unión de dos rectángulos.|
|[CRect::Ancho](#width)|Calcula el ancho `CRect`de .|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect::operador -](#operator_-)|Resta los desplazamientos `CRect` dados `CRect` de o `CRect`desinfla y devuelve el resultado .|
|[CRect::operador LPCRECT](#operator_lpcrect)|Convierte `CRect` en `LPCRECT`.|
|[CRect::operador LPRECT](#operator_lprect)|Convierte `CRect` en `LPRECT`.|
|[CRect::operador !o](#operator_neq)|Determina si `CRect` no es igual a un rectángulo.|
|[CRect::operador&amp;](#operator_amp)|Crea la `CRect` intersección de y `CRect`un rectángulo y devuelve el resultado .|
|[CRect::operador&amp;=](#operator_amp_eq)|Establece `CRect` igual a `CRect` la intersección de y un rectángulo.|
|[CRect::operador &#124;](#operator_or)|Crea la `CRect` unión de y `CRect`un rectángulo y devuelve el resultado .|
|[CRect::operador &#124;](#operator_or_eq)|Establece `CRect` igual a `CRect` la unión de y un rectángulo.|
|[CRect::operador +](#operator_add)|Agrega los desplazamientos `CRect` dados o `CRect` infla y `CRect`devuelve el resultado .|
|[CRect::operador +](#operator_add_eq)|Agrega los desfases `CRect` especificados `CRect`o infla .|
|[CRect::operador ?](#operator_eq)|Copia las dimensiones `CRect`de un rectángulo en .|
|[CRect::operador --](#operator_-_eq)|Resta los desfases especificados o `CRect` desinfla `CRect`.|
|[CRect::operador ?](#operator_eq_eq)|Determina si `CRect` es igual a un rectángulo.|

## <a name="remarks"></a>Observaciones

`CRect`también incluye funciones `CRect` miembro `RECT` para manipular objetos y estructuras de Windows.

Un `CRect` objeto se puede pasar como `RECT` un `LPCRECT`parámetro `LPRECT` de función dondequiera que una estructura, o se puede pasar.

> [!NOTE]
> Esta clase se deriva `tagRECT` de la estructura. (El `tagRECT` nombre es un nombre menos utilizado `RECT` para la estructura.) Esto significa que los`left` `top`miembros de datos ( `right`, , , `bottom`y ) de la `RECT` estructura son miembros de datos accesibles de `CRect`.

A `CRect` contiene variables miembro que definen los puntos superior izquierdo e inferior derecho de un rectángulo.

Al especificar `CRect`un , debe tener cuidado de construirlo para que se normaliza, es decir, de modo que el valor de la coordenada izquierda sea menor que el derecho y la parte superior sea menor que la inferior. Por ejemplo, una parte superior izquierda de (10,10) y la parte inferior derecha de (20,20) define un rectángulo normalizado, pero una parte superior izquierda de (20,20) y la parte inferior derecha de (10,10) define un rectángulo no normalizado. Si el rectángulo no está `CRect` normalizado, muchas funciones miembro pueden devolver resultados incorrectos. (Consulte [CRect::NormalizeRect](#normalizerect) para obtener una lista de estas funciones.) Antes de llamar a una función que requiere rectángulos normalizados, puede `NormalizeRect` normalizar rectángulos no normalizados llamando a la función.

Tenga cuidado al `CRect` manipular un con las funciones miembro [CDC::DPtoLP](../../mfc/reference/cdc-class.md#dptolp) y [CDC::LPtoDP.](../../mfc/reference/cdc-class.md#lptodp) Si el modo de asignación de un contexto de visualización `CDC::DPtoLP` es tal `CRect` que la extensión y es negativa, como en `MM_LOENGLISH`, entonces transformará la para que su parte superior sea mayor que la inferior. Funciones `Height` como `Size` y, a continuación, devolverán `CRect`valores negativos para el alto de la transformada, y el rectángulo no se normalizará.

Cuando se `CRect` utilizan operadores sobrecargados, `CRect`el primer operando debe ser un ; el segundo puede ser una estructura `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o un objeto.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagRECT`

`CRect`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes.h

## <a name="crectbottomright"></a><a name="bottomright"></a>CRect::BottomRight

Las coordenadas se devuelven como referencia a un `CRect`objeto [CPoint](cpoint-class.md) que se encuentra en .

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina inferior derecha del rectángulo.

### <a name="remarks"></a>Observaciones

Puede utilizar esta función para obtener o establecer la esquina inferior derecha del rectángulo. Establezca la esquina utilizando esta función en el lado izquierdo del operador de asignación.

### <a name="example"></a>Ejemplo

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

## <a name="crectcenterpoint"></a><a name="centerpoint"></a>CRect::CenterPoint

Calcula el punto `CRect` central de agregando los valores izquierdo y derecho y dividiendo por dos, y agregando los valores superior e inferior y dividiendo por dos.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CPoint` que es el `CRect`punto central de .

### <a name="example"></a>Ejemplo

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

## <a name="crectcopyrect"></a><a name="copyrect"></a>CRect::CopyRect

Copia `lpSrcRect` el `CRect`rectángulo en .

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parámetros

*lpSrcRect*<br/>
Apunta a la estructura `CRect` o objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que se va a copiar.

### <a name="example"></a>Ejemplo

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

## <a name="crectcrect"></a><a name="crect"></a>CRect::CRect

Construye un objeto `CRect`.

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>Parámetros

*l*<br/>
Especifica la posición `CRect`izquierda de .

*T*<br/>
Especifica la parte `CRect`superior de .

*R*<br/>
Especifica la posición `CRect`correcta de .

*B*<br/>
Especifica la parte `CRect`inferior de .

*srcRect*<br/>
Hace referencia a la estructura [RECT](/windows/win32/api/windef/ns-windef-rect) con las coordenadas de `CRect`.

*lpSrcRect*<br/>
Apunta a `RECT` la estructura con `CRect`las coordenadas de .

*Punto*<br/>
Especifica el punto de origen del rectángulo que se va a construir. Corresponde a la esquina superior izquierda.

*Tamaño*<br/>
Especifica el desplazamiento desde la esquina superior izquierda hasta la esquina inferior derecha del rectángulo que se va a construir.

*topLeft*<br/>
Especifica la posición superior `CRect`izquierda de .

*bottomRight*<br/>
Especifica la posición inferior `CRect`derecha de .

### <a name="remarks"></a>Observaciones

Si no se proporciona `left` `top`ningún `right`argumento, , , , y `bottom` los miembros no se inicializan.

Los `CRect``const RECT&`constructores `CRect``LPCRECT`( ) y ( ) realizan un [archivo CopyRect](#copyrect). Los otros constructores inicializan las variables miembro del objeto directamente.

### <a name="example"></a>Ejemplo

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

## <a name="crectdeflaterect"></a><a name="deflaterect"></a>CRect::DeflateRect

`DeflateRect`se desinfla `CRect` moviendo sus lados hacia su centro.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Especifica el número de unidades que se desinflan los lados izquierdo y derecho de `CRect`.

*y y*<br/>
Especifica el número de unidades que se `CRect`desinflan la parte superior e inferior de .

*Tamaño*<br/>
Un [SIZE](/windows/win32/api/windef/ns-windef-size) o [CSize](csize-class.md) que especifica el número `CRect`de unidades que se van a desinflar. El `cx` valor especifica el número de unidades para desinflar los lados izquierdo y derecho y el `cy` valor especifica el número de unidades para desinflar la parte superior e inferior.

*lpRect*<br/>
Apunta a una estructura `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o que especifica el número de unidades que se van a desinflar cada lado.

*l*<br/>
Especifica el número de unidades que se `CRect`desinflan el lado izquierdo de .

*T*<br/>
Especifica el número de unidades que `CRect`se desinflan la parte superior de .

*R*<br/>
Especifica el número de unidades que se `CRect`desinflan el lado derecho de .

*B*<br/>
Especifica el número de unidades que `CRect`se van a desinflar en la parte inferior de .

### <a name="remarks"></a>Observaciones

Para ello, `DeflateRect` añade unidades a la izquierda y a la parte superior y resta unidades de la derecha y la parte inferior. Los parámetros de `DeflateRect` son valores firmados; valores positivos `CRect` se desinflan y los valores negativos lo inflan.

Las dos primeras sobrecargas desinflan `CRect` ambos pares de lados opuestos de `cx`modo que su anchura total se reduce `cy`en dos veces *x* (o ) y su altura total se reduce dos veces *y* (o ). Las otras dos sobrecargas desinflan cada lado de `CRect` forma independiente de las otras.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

## <a name="crectequalrect"></a><a name="equalrect"></a>CRect::EqualRect

Determina si `CRect` es igual al rectángulo especificado.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura `CRect` u objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene las coordenadas de esquina superior izquierda e inferior derecha de un rectángulo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos rectángulos tienen los mismos valores superior, izquierdo, inferior y derecho; de lo contrario 0.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

## <a name="crectheight"></a><a name="height"></a>CRect::Altura

Calcula la altura `CRect` de restando el valor superior del valor inferior.

```
int Height() const throw();
```

### <a name="return-value"></a>Valor devuelto

La altura `CRect`de .

### <a name="remarks"></a>Observaciones

El valor resultante puede ser negativo.

> [!NOTE]
> El rectángulo debe normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

## <a name="crectinflaterect"></a><a name="inflaterect"></a>CRect::InflateRect

`InflateRect``CRect` inflaalmoviendo moviendo sus lados lejos de su centro.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Especifica el número de unidades para inflar `CRect`los lados izquierdo y derecho de .

*y y*<br/>
Especifica el número de unidades que se `CRect`inflan la parte superior e inferior de .

*Tamaño*<br/>
Un [SIZE](/windows/win32/api/windef/ns-windef-size) o [CSize](csize-class.md) que especifica el `CRect`número de unidades que se va a inflar . El `cx` valor especifica el número de unidades para inflar los lados izquierdo y derecho y el `cy` valor especifica el número de unidades para inflar la parte superior e inferior.

*lpRect*<br/>
Apunta a una estructura `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o que especifica el número de unidades para inflar cada lado.

*l*<br/>
Especifica el número de unidades para `CRect`inflar el lado izquierdo de .

*T*<br/>
Especifica el número de unidades que `CRect`se inflan en la parte superior de .

*R*<br/>
Especifica el número de unidades para `CRect`inflar el lado derecho de .

*B*<br/>
Especifica el número de unidades que `CRect`se inflan en la parte inferior de .

### <a name="remarks"></a>Observaciones

Para ello, `InflateRect` resta unidades de la izquierda y la parte superior y añade unidades a la derecha y a la parte inferior. Los parámetros de `InflateRect` son valores firmados; los valores `CRect` positivos inflan y los valores negativos lo desinflan.

Las dos primeras sobrecargas inflan `CRect` ambos pares de lados opuestos de `cx`modo que su anchura total se `cy`incrementa en dos veces *x* (o ) y su altura total se incrementa dos veces *y* (o ). Las otras dos sobrecargas inflan cada lado independientemente `CRect` de las otras.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

## <a name="crectintersectrect"></a><a name="intersectrect"></a>CRect::IntersectRect

Hace `CRect` un igual a la intersección de dos rectángulos existentes.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a una estructura `CRect` o objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a `RECT` una `CRect` estructura u objeto que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la intersección no está vacía; 0 si la intersección está vacía.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande contenido en ambos rectángulos existentes.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

## <a name="crectisrectempty"></a><a name="isrectempty"></a>CRect::IsRectEmpty

Determina si `CRect` está vacío.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CRect` cero si está vacío; 0 `CRect` si no está vacío.

### <a name="remarks"></a>Observaciones

Un rectángulo está vacío si el ancho y/o alto son 0 o negativos. Difiere de `IsRectNull`, que determina si todas las coordenadas del rectángulo son cero.

> [!NOTE]
> El rectángulo debe normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

## <a name="crectisrectnull"></a><a name="isrectnull"></a>CRect::IsRectNull

Determina si los valores superior, izquierdo, `CRect` inferior y derecho de son todos iguales a 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de `CRect`cero si los valores 's top, left, bottom y right son todos iguales a 0; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Difiere de `IsRectEmpty`, que determina si el rectángulo está vacío.

### <a name="example"></a>Ejemplo

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

## <a name="crectmovetox"></a><a name="movetox"></a>CRect::MoveToX

Llame a esta función para mover el rectángulo a la coordenada x absoluta especificada por *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Coordenada x absoluta para la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

## <a name="crectmovetoxy"></a><a name="movetoxy"></a>CRect::MoveToxY

Llame a esta función para mover el rectángulo a las coordenadas x e y absolutas especificadas.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Coordenada x absoluta para la esquina superior izquierda del rectángulo.

*y y*<br/>
Coordenada y absoluta para la esquina superior izquierda del rectángulo.

*Punto*<br/>
Estructura `POINT` que especifica la esquina superior izquierda absoluta del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

## <a name="crectmovetoy"></a><a name="movetoy"></a>CRect::MoveToY

Llame a esta función para mover el rectángulo a la coordenada y absoluta especificada por *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parámetros

*y y*<br/>
Coordenada y absoluta para la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

## <a name="crectnormalizerect"></a><a name="normalizerect"></a>CRect::NormalizeRect

Normaliza `CRect` para que tanto la altura como la anchura sean positivas.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Observaciones

El rectángulo se normaliza para el posicionamiento del cuarto cuadrante, que Windows utiliza normalmente para las coordenadas. `NormalizeRect`compara los valores superior e inferior, y los intercambia si la parte superior es mayor que la inferior. Del mismo modo, intercambia los valores izquierdo y derecho si la izquierda es mayor que la derecha. Esta función es útil cuando se trata de diferentes modos de asignación y rectángulos invertidos.

> [!NOTE]
> Las `CRect` siguientes funciones miembro requieren rectángulos normalizados para funcionar correctamente: [Alto](#height), [Ancho](#width), [Tamaño](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [operador](#operator_eq_eq), [operador !](#operator_neq), [operador &#124;](#operator_or), [operador &#124;](#operator_or_eq), operador [&](#operator_amp), y [operador &](#operator_amp_eq).

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

## <a name="crectoffsetrect"></a><a name="offsetrect"></a>CRect::OffsetRect

Se `CRect` mueve por los desplazamientos especificados.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parámetros

*X*<br/>
Especifica la cantidad que se va a mover a la izquierda o a la derecha. Debe ser negativo moverse a la izquierda.

*y y*<br/>
Especifica la cantidad que se va a mover hacia arriba o hacia abajo. Debe ser negativo subir.

*Punto*<br/>
Contiene una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](cpoint-class.md) que especifica ambas dimensiones por las que se va a mover.

*Tamaño*<br/>
Contiene una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](csize-class.md) que especifica ambas dimensiones por las que se va a mover.

### <a name="remarks"></a>Observaciones

Mueve `CRect` *x* unidades a lo largo del eje X y las unidades *y* a lo largo del eje Y. Los parámetros *x* e *y* son valores con signo, por lo que `CRect` se pueden mover a la izquierda o a la derecha y hacia arriba o hacia abajo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

## <a name="crectoperator-lpcrect-converts-a-crect-to-an-lpcrect"></a><a name="operator_lpcrect"></a>CRect::operator LPCRECT Convierte `CRect` a en un [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Observaciones

Cuando se utiliza esta función, no se**&** necesita el operador address-of ( ). Este operador se utilizará automáticamente `CRect` cuando pase un objeto `LPCRECT`a una función que espera un archivo .

## <a name="crectoperator-lprect"></a><a name="operator_lprect"></a>CRect::operador LPRECT

Convierte `CRect` a en un [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Observaciones

Cuando se utiliza esta función, no se**&** necesita el operador address-of ( ). Este operador se utilizará automáticamente `CRect` cuando pase un objeto `LPRECT`a una función que espera un archivo .

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::operator LPCRECT](#operator_lpcrect).

## <a name="crectoperator-"></a><a name="operator_eq"></a>CRect::operador ?

Asigna *srcRect* `CRect`a .

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parámetros

*srcRect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o .

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

## <a name="crectoperator-"></a><a name="operator_eq_eq"></a>CRect::operador ?

Determina si `rect` es `CRect` igual a comparando las coordenadas de sus esquinas superior izquierda e inferior derecha.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es igual; de lo contrario 0.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

## <a name="crectoperator-"></a><a name="operator_neq"></a>CRect::operador !o

Determina si *rect* no `CRect` es igual a comparando las coordenadas de sus esquinas superior izquierda e inferior derecha.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no es igual; de lo contrario 0.

### <a name="remarks"></a>Observaciones

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

## <a name="crectoperator-"></a><a name="operator_add_eq"></a>CRect::operador +

Las dos primeras `CRect` sobrecargas se mueven por los desplazamientos especificados.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](cpoint-class.md) que especifica el número de unidades para mover el rectángulo.

*Tamaño*<br/>
Una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o [cSize](csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*lpRect*<br/>
Apunta a una estructura `CRect` u objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene el `CRect`número de unidades para inflar cada lado de .

### <a name="remarks"></a>Observaciones

Los valores *x* *y* e y `cx` `cy`(o y) `CRect`del parámetro se agregan a .

La tercera sobrecarga `CRect` se infla por el número de unidades especificadas en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-_eq"></a>CRect::operador --

Las dos primeras `CRect` sobrecargas se mueven por los desplazamientos especificados.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Una estructura [POINT](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](cpoint-class.md) que especifica el número de unidades para mover el rectángulo.

*Tamaño*<br/>
Una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o [cSize](csize-class.md) objeto que especifica el número de unidades para mover el rectángulo.

*lpRect*<br/>
Apunta a una estructura `CRect` u objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene el `CRect`número de unidades que se van a desinflar a cada lado de .

### <a name="remarks"></a>Observaciones

Los valores *x* *y* e y `cx` `cy`(o y) `CRect`del parámetro se restan de .

La tercera sobrecarga `CRect` se desinfla por el número de unidades especificadas en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect).

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp_eq"></a>CRect::operador&amp;=

Establece `CRect` igual a `CRect` la `rect`intersección de y .

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene un [RECT](/windows/win32/api/windef/ns-windef-rect) o `CRect`.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande que se encuentra en ambos rectángulos.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::IntersectRect](#intersectrect).

## <a name="crectoperator-124"></a><a name="operator_or_eq"></a>CRect::operador &#124;

Establece `CRect` igual a `CRect` la `rect`unión de y .

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene `CRect` un o [RECT](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Observaciones

La unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

## <a name="crectoperator-"></a><a name="operator_add"></a>CRect::operador +

Las dos primeras `CRect` sobrecargas devuelven `CRect` un objeto que es igual a desplazado por los desplazamientos especificados.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Estructura [POINT](/windows/win32/api/windef/ns-windef-point) o [cPoint](cpoint-class.md) objeto que especifica el número de unidades para mover el valor devuelto.

*Tamaño*<br/>
Una estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](csize-class.md) que especifica el número de unidades para mover el valor devuelto.

*lpRect*<br/>
Apunta a una estructura `CRect` u objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene el número de unidades para inflar cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultado de moverse `CRect` o inflar se mueve por el número de unidades especificado en el parámetro.

### <a name="remarks"></a>Observaciones

Los parámetros *x* e `cx` *y* (o y) `cy`del parámetro se agregan a `CRect`la posición 's.

La tercera sobrecarga `CRect` devuelve un `CRect` nuevo que es igual a inflado por el número de unidades especificado en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

## <a name="crectoperator--"></a><a name="operator_-"></a>CRect::operador -

Las dos primeras `CRect` sobrecargas devuelven `CRect` un objeto que es igual a desplazado por los desplazamientos especificados.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Estructura [POINT](/windows/win32/api/windef/ns-windef-point) u `CPoint` objeto POINT que especifica el número de unidades para mover el valor devuelto.

*Tamaño*<br/>
Estructura [SIZE](/windows/win32/api/windef/ns-windef-size) o `CSize` objeto SIZE que especifica el número de unidades para mover el valor devuelto.

*lpRect*<br/>
Apunta a una estructura `CRect` u objeto [RECT](/windows/win32/api/windef/ns-windef-rect) que contiene el número de unidades que se van a desinflar a cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultado de moverse `CRect` o desinflarse por el número de unidades especificadas en el parámetro.

### <a name="remarks"></a>Observaciones

Los parámetros *x* e `cx` *y* (o y) `CRect` `cy`del parámetro se restan de la posición de 's.

La tercera sobrecarga `CRect` devuelve un `CRect` nuevo que es igual a desinflado por el número de unidades especificado en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect), no [SubtractRect](#subtractrect).

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

## <a name="crectoperator-amp"></a><a name="operator_amp"></a>CRect::operador&amp;

Devuelve `CRect` a que es `CRect` la intersección de y *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [RECT](/windows/win32/api/windef/ns-windef-rect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

A `CRect` que es `CRect` la intersección de y *rect2*.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande que se encuentra en ambos rectángulos.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

## <a name="crectoperator-124"></a><a name="operator_or"></a>CRect::operador &#124;

Devuelve `CRect` a que es `CRect` la unión de y *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [RECT](/windows/win32/api/windef/ns-windef-rect) o `CRect`.

### <a name="return-value"></a>Valor devuelto

A `CRect` que es `CRect` la unión de y *rect2*.

### <a name="remarks"></a>Observaciones

La unión es el rectángulo más pequeño que contiene ambos rectángulos.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectptinrect"></a><a name="ptinrect"></a>CRect::PtInRect

Determina si el punto especificado `CRect`se encuentra dentro de .

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*Punto*<br/>
Contiene un [POINT](/windows/win32/api/windef/ns-windef-point) estructura o [CPoint](cpoint-class.md) objeto.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `CRect`el punto se encuentra dentro de ; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Un punto `CRect` está dentro si se encuentra en el lado izquierdo o superior o está dentro de los cuatro lados. Un punto en el lado `CRect`derecho o inferior está fuera.

> [!NOTE]
> El rectángulo debe normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

## <a name="crectsetrect"></a><a name="setrect"></a>CRect::SetRect

Establece las `CRect` dimensiones de las coordenadas especificadas.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parámetros

*x1*<br/>
Especifica la coordenada x de la esquina superior izquierda.

*y1*<br/>
Especifica la coordenada y de la esquina superior izquierda.

*x2*<br/>
Especifica la coordenada x de la esquina inferior derecha.

*y2*<br/>
Especifica la coordenada y de la esquina inferior derecha.

### <a name="example"></a>Ejemplo

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

## <a name="crectsetrectempty"></a><a name="setrectempty"></a>CRect::SetRectEmpty

Crea `CRect` un rectángulo nulo estableciendo todas las coordenadas en cero.

```
void SetRectEmpty() throw();
```

### <a name="example"></a>Ejemplo

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

## <a name="crectsize"></a><a name="size"></a>CRect::SIZE

Los `cx` `cy` miembros y del valor devuelto `CRect`contienen el alto y el ancho de .

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valor devuelto

Un [CSize](csize-class.md) objeto que `CRect`contiene el tamaño de .

### <a name="remarks"></a>Observaciones

La altura o la anchura pueden ser negativas.

> [!NOTE]
> El rectángulo debe normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

## <a name="crectsubtractrect"></a><a name="subtractrect"></a>CRect::SubtractRect

Hace que las `CRect` dimensiones de `lpRectSrc2` igual `lpRectSrc1`a la resta de from .

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRectSrc1*<br/>
Apunta a la estructura `CRect` o objeto [RECT](/windows/win32/api/windef/ns-windef-rect) del que se va a restar un rectángulo.

*lpRectSrc2*<br/>
Apunta a `RECT` la `CRect` estructura u objeto que se va a restar del rectángulo al que apunta el parámetro *lpRectSrc1.*

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La resta es el rectángulo más pequeño que contiene todos los puntos de *lpRectScr1* que no están en la intersección de *lpRectScr1* y *lpRectScr2*.

El rectángulo especificado por *lpRectSrc1* no cambiará si el rectángulo especificado por *lpRectSrc2* no se superpone completamente al rectángulo especificado por *lpRectSrc1* en al menos una de las direcciones x o y.

Por ejemplo, si *lpRectSrc1* fueran (10,10, 100,100) y *lpRectSrc2* (50,50, 150,150), el rectángulo al que apunta *lpRectSrc1* no cambiaría cuando se devolviera la función. Si *lpRectSrc1* fueran (10,10, 100,100) y *lpRectSrc2* eran (50,10, 150,150), sin embargo, el rectángulo señalado por *lpRectSrc1* contendría las coordenadas (10,10, 50,100) cuando se devolviera la función.

`SubtractRect`no es lo mismo que [el operador -](#operator_-) ni el operador [-](#operator_-_eq). Ninguno de estos `SubtractRect`operadores llama a .

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

## <a name="crecttopleft"></a><a name="topleft"></a>CRect::TopLeft

Las coordenadas se devuelven como referencia a un `CRect`objeto [CPoint](cpoint-class.md) que se encuentra en .

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Valor devuelto

Las coordenadas de la esquina superior izquierda del rectángulo.

### <a name="remarks"></a>Observaciones

Puede utilizar esta función para obtener o establecer la esquina superior izquierda del rectángulo. Establezca la esquina utilizando esta función en el lado izquierdo del operador de asignación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect::CenterPoint](#centerpoint).

## <a name="crectunionrect"></a><a name="unionrect"></a>CRect::UnionRect

Hace que `CRect` las dimensiones sean iguales a la unión de los dos rectángulos de origen.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a un `CRect` [RECT](/windows/win32/api/windef/ns-windef-rect) o que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a `RECT` `CRect` un o que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la unión no está vacía; 0 si la unión está vacía.

### <a name="remarks"></a>Observaciones

La unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

Windows omite las dimensiones de un rectángulo vacío; es decir, un rectángulo que no tiene altura o no tiene anchura.

> [!NOTE]
> Ambos rectángulos deben normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

## <a name="crectwidth"></a><a name="width"></a>CRect::Ancho

Calcula el ancho `CRect` de restando el valor izquierdo del valor derecho.

```
int Width() const throw();
```

### <a name="return-value"></a>Valor devuelto

La anchura `CRect`de .

### <a name="remarks"></a>Observaciones

El ancho puede ser negativo.

> [!NOTE]
> El rectángulo debe normalizarse o esta función puede fallar. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Consulte también

[Clase CPoint](cpoint-class.md)<br/>
[Clase CSize](csize-class.md)<br/>
[Rect](/windows/win32/api/windef/ns-windef-rect)
