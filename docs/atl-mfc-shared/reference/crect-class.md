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
ms.openlocfilehash: 13f86c411cca98f5817d1b3b2d9162ae8af8b734
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866537"
---
# <a name="crect-class"></a>Clase CRect

Similar a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) de Windows.

## <a name="syntax"></a>Sintaxis

```
class CRect : public tagRECT
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect:: CRect](#crect)|Construye un objeto `CRect`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect:: BottomRight](#bottomright)|Devuelve el punto inferior derecho de `CRect`.|
|[CRect:: CenterPoint](#centerpoint)|Devuelve el CenterPoint de `CRect`.|
|[CRect:: CopyRect](#copyrect)|Copia las dimensiones de un rectángulo de origen en `CRect`.|
|[CRect::D eflateRect](#deflaterect)|Disminuye el ancho y el alto de `CRect`.|
|[CRect:: EqualRect](#equalrect)|Determina si `CRect` es igual al rectángulo especificado.|
|[CRect:: height](#height)|Calcula el alto de `CRect`.|
|[CRect:: InflateRect](#inflaterect)|Aumenta el ancho y el alto de `CRect`.|
|[CRect:: IntersectRect](#intersectrect)|Establece `CRect` igual a la intersección de dos rectángulos.|
|[CRect:: IsRectEmpty](#isrectempty)|Determina si `CRect` está vacío. `CRect` está vacío si el ancho o el alto son 0.|
|[CRect:: IsRectNull](#isrectnull)|Determina si las variables miembro `top`, `bottom`, `left`y `right` son iguales a 0.|
|[CRect:: MoveToX](#movetox)|Mueve `CRect` a la coordenada x especificada.|
|[CRect:: MoveToXY](#movetoxy)|Mueve `CRect` a las coordenadas x e y especificadas.|
|[CRect:: MoveToY](#movetoy)|Mueve `CRect` a la coordenada y especificada.|
|[CRect:: NormalizeRect](#normalizerect)|Normaliza el alto y el ancho de `CRect`.|
|[CRect:: OffsetRect](#offsetrect)|Mueve `CRect` en función de los desplazamientos especificados.|
|[CRect::P tInRect](#ptinrect)|Determina si el punto especificado se encuentra dentro de `CRect`.|
|[CRect:: SetRect](#setrect)|Establece las dimensiones de `CRect`.|
|[CRect:: SetRectEmpty](#setrectempty)|Establece `CRect` en un rectángulo vacío (todas las coordenadas son iguales a 0).|
|[CRect:: Size](#size)|Calcula el tamaño de `CRect`.|
|[CRect:: SubtractRect](#subtractrect)|Resta un rectángulo de otro.|
|[CRect:: enleft](#topleft)|Devuelve el punto superior izquierdo de `CRect`.|
|[CRect:: UnionRect](#unionrect)|Establece `CRect` igual a la Unión de dos rectángulos.|
|[CRect:: width](#width)|Calcula el ancho de `CRect`.|

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CRect:: Operator-](#operator_-)|Resta los desplazamientos especificados de `CRect` o desinfla `CRect` y devuelve el `CRect`resultante.|
|[CRect:: Operator LPCRECT](#operator_lpcrect)|Convierte `CRect` en `LPCRECT`.|
|[CRect:: Operator LPRECT](#operator_lprect)|Convierte `CRect` en `LPRECT`.|
|[CRect:: Operator! =](#operator_neq)|Determina si `CRect` no es igual que un rectángulo.|
|[CRect:: Operator &amp;](#operator_amp)|Crea la intersección de `CRect` y un rectángulo y devuelve el `CRect`resultante.|
|[CRect:: Operator &amp;=](#operator_amp_eq)|Establece `CRect` igual a la intersección de `CRect` y un rectángulo.|
|[CRect:: Operator&#124;](#operator_or)|Crea la Unión de `CRect` y un rectángulo y devuelve el `CRect`resultante.|
|[CRect:: Operator &#124;=](#operator_or_eq)|Establece `CRect` igual a la Unión de `CRect` y un rectángulo.|
|[CRect:: Operator +](#operator_add)|Agrega los desplazamientos especificados a `CRect` o infla `CRect` y devuelve el `CRect`resultante.|
|[CRect:: Operator + =](#operator_add_eq)|Agrega los desplazamientos especificados a `CRect` o infla `CRect`.|
|[CRect:: Operator =](#operator_eq)|Copia las dimensiones de un rectángulo en `CRect`.|
|[CRect:: Operator-=](#operator_-_eq)|Resta los desplazamientos especificados de `CRect` o desinfla `CRect`.|
|[CRect:: Operator = =](#operator_eq_eq)|Determina si `CRect` es igual a un rectángulo.|

## <a name="remarks"></a>Observaciones

`CRect` también incluye funciones miembro para manipular objetos `CRect` y estructuras `RECT` de Windows.

Un objeto `CRect` se puede pasar como un parámetro de función siempre que se pueda pasar una estructura `RECT`, `LPCRECT`o `LPRECT`.

> [!NOTE]
> Esta clase se deriva de la estructura `tagRECT`. (El nombre `tagRECT` es un nombre que se usa con menos frecuencia para la estructura de `RECT`). Esto significa que los miembros de datos (`left`, `top`, `right`y `bottom`) de la estructura `RECT` son miembros de datos accesibles de `CRect`.

Un `CRect` contiene variables de miembro que definen los puntos superior izquierdo e inferior derecho de un rectángulo.

Al especificar un `CRect`, debe tener cuidado de construirlo para que se normalice, es decir, que el valor de la coordenada izquierda sea menor que el derecho y que la parte superior sea menor que la parte inferior. Por ejemplo, una parte superior izquierda de (10, 10) e inferior derecha de (20, 20) define un rectángulo normalizado, pero una parte superior izquierda de (20, 20) e inferior derecha de (10, 10) define un rectángulo no normalizado. Si no se normaliza el rectángulo, muchas `CRect` funciones miembro pueden devolver resultados incorrectos. (Vea [CRect:: NormalizeRect](#normalizerect) para obtener una lista de estas funciones). Antes de llamar a una función que requiera rectángulos normalizados, puede normalizar los rectángulos no normalizados llamando a la función `NormalizeRect`.

Tenga precaución al manipular un `CRect` con las funciones miembro [CDC::D ptolp](../../mfc/reference/cdc-class.md#dptolp) y [CDC:: LPtoDP](../../mfc/reference/cdc-class.md#lptodp) . Si el modo de asignación de un contexto de presentación es tal que la extensión y es negativa, como en `MM_LOENGLISH`, `CDC::DPtoLP` transformará el `CRect` de forma que su superior sea mayor que la parte inferior. Las funciones como `Height` y `Size` devolverán valores negativos para el alto de la `CRect`transformada y el rectángulo no se normalizará.

Al usar operadores `CRect` sobrecargados, el primer operando debe ser un `CRect`; el segundo puede ser una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o un objeto `CRect`.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tagRECT`

`CRect`

## <a name="requirements"></a>Requisitos

**Encabezado:** atltypes. h

##  <a name="bottomright"></a>CRect:: BottomRight

Las coordenadas se devuelven como una referencia a un objeto [CPoint](cpoint-class.md) contenido en `CRect`.

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>Valor devuelto

Coordenadas de la esquina inferior derecha del rectángulo.

### <a name="remarks"></a>Observaciones

Puede usar esta función para obtener o establecer la esquina inferior derecha del rectángulo. Establezca la esquina mediante esta función en el lado izquierdo del operador de asignación.

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

##  <a name="centerpoint"></a>CRect:: CenterPoint

Calcula el CenterPoint de `CRect` agregando los valores izquierdo y derecho, y dividiendo por dos, y agregando los valores superior e inferior, y dividiendo por dos.

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>Valor devuelto

Objeto `CPoint` que es el CenterPoint de `CRect`.

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

##  <a name="copyrect"></a>CRect:: CopyRect

Copia el rectángulo `lpSrcRect` en `CRect`.

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>Parámetros

*lpSrcRect*<br/>
Apunta a la estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o al `CRect` objeto que se va a copiar.

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

##  <a name="crect"></a>CRect:: CRect

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
Especifica la posición izquierda de `CRect`.

*t*<br/>
Especifica la parte superior de `CRect`.

*r*<br/>
Especifica la posición derecha de `CRect`.

*b*<br/>
Especifica la parte inferior de `CRect`.

*srcRect*<br/>
Hace referencia a la estructura [Rect](/windows/win32/api/windef/ns-windef-rect) con las coordenadas de `CRect`.

*lpSrcRect*<br/>
Apunta a la estructura `RECT` con las coordenadas de `CRect`.

*Elija*<br/>
Especifica el punto de origen del rectángulo que se va a construir. Corresponde a la esquina superior izquierda.

*size*<br/>
Especifica el desplazamiento de la esquina superior izquierda a la esquina inferior derecha del rectángulo que se va a construir.

*a la izquierda*<br/>
Especifica la posición superior izquierda de `CRect`.

*PivotDetailRange*<br/>
Especifica la posición inferior derecha de `CRect`.

### <a name="remarks"></a>Observaciones

Si no se especifica ningún argumento, no se inicializan los miembros `left`, `top`, `right`y `bottom`.

Los constructores `CRect`(`const RECT&`) y `CRect`(`LPCRECT`) realizan una [CopyRect](#copyrect). Los demás constructores inicializan directamente las variables de miembro del objeto.

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

##  <a name="deflaterect"></a>CRect::D eflateRect

`DeflateRect` desinfla `CRect` moviendo sus lados hacia su centro.

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades para DEFLATE los lados izquierdo y derecho de `CRect`.

*y*<br/>
Especifica el número de unidades para DEFLATE la parte superior e inferior de `CRect`.

*size*<br/>
[Tamaño](/windows/win32/api/windef/ns-windef-size) o [CSize](csize-class.md) que especifica el número de unidades que se van a deinflar `CRect`. El valor `cx` especifica el número de unidades para DEFLATE los lados izquierdo y derecho, y el valor `cy` especifica el número de unidades que se van a deflatar en la parte superior e inferior.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` que especifica el número de unidades que se va a deflatar cada lado.

*l*<br/>
Especifica el número de unidades para DEFLATE el lado izquierdo de `CRect`.

*t*<br/>
Especifica el número de unidades para DEFLATE la parte superior de `CRect`.

*r*<br/>
Especifica el número de unidades para DEFLATE el lado derecho de `CRect`.

*b*<br/>
Especifica el número de unidades para DEFLATE la parte inferior de `CRect`.

### <a name="remarks"></a>Observaciones

Para ello, `DeflateRect` agrega unidades a la izquierda y a la parte superior y resta las unidades de la parte derecha e inferior. Los parámetros de `DeflateRect` son valores con signo; los valores positivos deflaten `CRect` y los valores negativos para inflarlos.

Las dos primeras sobrecargas detienen ambos pares de lados opuestos de `CRect` para que el ancho total se reduzca en dos veces *x* (o `cx`) y su alto total se reduzca en dos veces *y* (o `cy`). Las otras dos sobrecargas deflatan cada lado de `CRect` independientemente de las demás.

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

##  <a name="equalrect"></a>CRect:: EqualRect

Determina si `CRect` es igual al rectángulo especificado.

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` objeto que contiene las coordenadas de la esquina superior izquierda e inferior derecha de un rectángulo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si los dos rectángulos tienen los mismos valores superior, izquierdo, inferior y derecho. de lo contrario, es 0.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

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

##  <a name="height"></a>CRect:: height

Calcula el alto de `CRect` restando el valor superior del valor inferior.

```
int Height() const throw();
```

### <a name="return-value"></a>Valor devuelto

Alto de `CRect`.

### <a name="remarks"></a>Observaciones

El valor resultante puede ser negativo.

> [!NOTE]
>  El rectángulo debe normalizarse o puede producirse un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>CRect:: InflateRect

`InflateRect` infla `CRect` moviendo sus lados de su centro.

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica el número de unidades para inflar los lados izquierdo y derecho de `CRect`.

*y*<br/>
Especifica el número de unidades para inflar la parte superior e inferior de `CRect`.

*size*<br/>
[Tamaño](/windows/win32/api/windef/ns-windef-size) o [CSize](csize-class.md) que especifica el número de unidades que se van a aumentar `CRect`. El valor `cx` especifica el número de unidades que se van a aumentar los lados izquierdo y derecho, y el valor `cy` especifica el número de unidades que se van a aumentar e inferior.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` que especifica el número de unidades que se van a aumentar cada lado.

*l*<br/>
Especifica el número de unidades para aumentar el lado izquierdo de `CRect`.

*t*<br/>
Especifica el número de unidades para inflar la parte superior de `CRect`.

*r*<br/>
Especifica el número de unidades para aumentar el lado derecho de `CRect`.

*b*<br/>
Especifica el número de unidades para inflar la parte inferior de `CRect`.

### <a name="remarks"></a>Observaciones

Para ello, `InflateRect` resta unidades de la izquierda y la parte superior, y agrega unidades a la parte derecha e inferior. Los parámetros de `InflateRect` son valores con signo; los valores positivos implanan `CRect` y los valores negativos lo deflaten.

Las dos primeras sobrecargas inflan ambos pares de lados opuestos de `CRect` de modo que el ancho total se aumente en dos veces *x* (o `cx`) y su alto total se incremente en dos veces *y* (o `cy`). Las otras dos sobrecargas implanan cada lado de `CRect` independientemente de las demás.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>CRect:: IntersectRect

Hace que un `CRect` igual a la intersección de dos rectángulos existentes.

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o a `CRect` objeto que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a una estructura `RECT` o a un objeto `CRect` que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la intersección no está vacía; 0 si la intersección está vacía.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande contenido en los dos rectángulos existentes.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

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

##  <a name="isrectempty"></a>CRect:: IsRectEmpty

Determina si `CRect` está vacío.

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si `CRect` está vacío; 0 si `CRect` no está vacío.

### <a name="remarks"></a>Observaciones

Un rectángulo está vacío si el ancho o el alto son 0 o negativo. Difiere de `IsRectNull`, que determina si todas las coordenadas del rectángulo son cero.

> [!NOTE]
>  El rectángulo debe normalizarse o puede producirse un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>CRect:: IsRectNull

Determina si los valores superior, izquierdo, inferior y derecho de `CRect` son iguales a 0.

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el valor de los valores superior, izquierdo, inferior y derecho de `CRect`es igual a 0; de lo contrario, es 0.

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

##  <a name="movetox"></a>CRect:: MoveToX

Llame a esta función para desplace el rectángulo a la coordenada x absoluta especificada por *x*.

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x absoluta de la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>CRect:: MoveToXY

Llame a esta función para desplace el rectángulo a las coordenadas x e y absolutas especificadas.

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Coordenada x absoluta de la esquina superior izquierda del rectángulo.

*y*<br/>
Coordenada y absoluta de la esquina superior izquierda del rectángulo.

*Elija*<br/>
Estructura `POINT` que especifica la esquina superior izquierda absoluta del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>CRect:: MoveToY

Llame a esta función para desplace el rectángulo a la coordenada y absoluta especificada por *y*.

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>Parámetros

*y*<br/>
Coordenada y absoluta de la esquina superior izquierda del rectángulo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>CRect:: NormalizeRect

Normaliza `CRect` de modo que el alto y el ancho sean positivos.

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>Observaciones

El rectángulo se normaliza para el posicionamiento del cuarto cuadrante, que normalmente usa Windows para las coordenadas. `NormalizeRect` compara los valores superior e inferior, y los intercambia si la parte superior es mayor que la parte inferior. Del mismo modo, intercambia los valores izquierdo y derecho si la izquierda es mayor que la derecha. Esta función es útil cuando se trabaja con diferentes modos de asignación y rectángulos invertidos.

> [!NOTE]
> Las siguientes funciones miembro de `CRect` requieren rectángulos normalizados para que funcionen correctamente [: height](#height), [width](#width), [size](#size), [IsRectEmpty](#isrectempty), [PtInRect](#ptinrect), [EqualRect](#equalrect), [UnionRect](#unionrect), [IntersectRect](#intersectrect), [SubtractRect](#subtractrect), [Operator = =](#operator_eq_eq), [Operator! =](#operator_neq), [ &#124;Operator, Operator ](#operator_or) [ &#124;=](#operator_or_eq), [Operator &](#operator_amp)y [Operator & =](#operator_amp_eq).

### <a name="example"></a>Ejemplo

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>CRect:: OffsetRect

Mueve `CRect` en función de los desplazamientos especificados.

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>Parámetros

*x*<br/>
Especifica la cantidad de desplazamiento a la izquierda o a la derecha. Debe ser negativo para moverse a la izquierda.

*y*<br/>
Especifica la cantidad de movimiento hacia arriba o hacia abajo. Debe ser negativo para subir.

*Elija*<br/>
Contiene una estructura de [punto](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](cpoint-class.md) que especifica las dos dimensiones por las que se va a desplace.

*size*<br/>
Contiene una estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o un objeto [CSize](csize-class.md) que especifica las dos dimensiones por las que se va a desplace.

### <a name="remarks"></a>Observaciones

Mueve `CRect`unidades *x* a lo largo del eje x y las unidades *y* a lo largo del eje y. Los parámetros x *e y son* valores con signo, por lo que `CRect` puede moverse hacia la izquierda o hacia la derecha y hacia arriba o hacia abajo.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect:: Operator LPCRECT convierte una `CRect` en una [LPCRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>Observaciones

Cuando se usa esta función, no se necesita el operador Address-of ( **&** ). Este operador se usará automáticamente al pasar un objeto `CRect` a una función que espera un `LPCRECT`.

##  <a name="operator_lprect"></a>CRect:: Operator LPRECT

Convierte un `CRect` en un [LPRECT](../../mfc/reference/data-types-mfc.md).

```
operator LPRECT() throw();
```

### <a name="remarks"></a>Observaciones

Cuando se usa esta función, no se necesita el operador Address-of ( **&** ). Este operador se usará automáticamente al pasar un objeto `CRect` a una función que espera un `LPRECT`.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect:: Operator LPCRECT](#operator_lpcrect).

##  <a name="operator_eq"></a>CRect:: Operator =

Asigna *srcRect* a `CRect`.

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>Parámetros

*srcRect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect:: Operator = =

Determina si `rect` es igual a `CRect` comparando las coordenadas de las esquinas superior izquierda e inferior derecha.

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si es igual a; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

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

##  <a name="operator_neq"></a>CRect:: Operator! =

Determina si *Rect* no es igual a `CRect` comparando las coordenadas de las esquinas superior izquierda e inferior derecha.

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Hace referencia a un rectángulo de origen. Puede ser un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si no es igual a; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

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

##  <a name="operator_add_eq"></a>CRect:: Operator + =

Las dos primeras sobrecargas mueven `CRect` por los desplazamientos especificados.

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
Estructura de [punto](/windows/win32/api/windef/ns-windef-point) o objeto [CPoint](cpoint-class.md) que especifica el número de unidades que se va a desplace el rectángulo.

*size*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o objeto [CSize](csize-class.md) que especifica el número de unidades que se va a desplace el rectángulo.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` objeto que contiene el número de unidades que se va a aumentar cada lado de `CRect`.

### <a name="remarks"></a>Observaciones

Los valores *x* e y *(o* `cx` y `cy`) del parámetro se agregan a `CRect`.

La tercera sobrecarga aumenta `CRect` por el número de unidades especificado en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect:: Operator-=

Las dos primeras sobrecargas mueven `CRect` por los desplazamientos especificados.

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
Estructura de [punto](/windows/win32/api/windef/ns-windef-point) o objeto [CPoint](cpoint-class.md) que especifica el número de unidades que se va a desplace el rectángulo.

*size*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o objeto [CSize](csize-class.md) que especifica el número de unidades que se va a desplace el rectángulo.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` objeto que contiene el número de unidades que se va a deflatar cada lado de `CRect`.

### <a name="remarks"></a>Observaciones

Los valores *x* *e y* (o `cx` y `cy`) del parámetro se restan de `CRect`.

La tercera sobrecarga desinfla `CRect` por el número de unidades especificado en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect).

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect:: Operator &amp;=

Establece `CRect` igual a la intersección de `CRect` y `rect`.

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande que se encuentra en ambos rectángulos.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect:: IntersectRect](#intersectrect).

##  <a name="operator_or_eq"></a>CRect:: Operator &#124;=

Establece `CRect` igual a la Unión de `CRect` y `rect`.

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>Parámetros

*Rect*<br/>
Contiene un `CRect` o un [Rect](/windows/win32/api/windef/ns-windef-rect).

### <a name="remarks"></a>Observaciones

La Unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect:: Operator +

Las dos primeras sobrecargas devuelven un objeto `CRect` que es igual a `CRect` desplazados por los desplazamientos especificados.

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
Estructura de [punto](/windows/win32/api/windef/ns-windef-point) o objeto [CPoint](cpoint-class.md) que especifica el número de unidades que se va a devolver el valor devuelto.

*size*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o objeto [CSize](csize-class.md) que especifica el número de unidades que se va a devolver el valor devuelto.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o a `CRect` objeto que contiene el número de unidades que se va a aumentar cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultante de mover o inflar `CRect` por el número de unidades especificadas en el parámetro.

### <a name="remarks"></a>Observaciones

Los parámetros *x* e y *(o* `cx` y `cy`) del parámetro se agregan a la posición de `CRect`.

La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` inflado por el número de unidades especificado en cada miembro del parámetro.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect:: Operator-

Las dos primeras sobrecargas devuelven un objeto `CRect` que es igual a `CRect` desplazados por los desplazamientos especificados.

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
Estructura de [punto](/windows/win32/api/windef/ns-windef-point) o objeto de `CPoint` que especifica el número de unidades para el que se va a desplace el valor devuelto.

*size*<br/>
Estructura de [tamaño](/windows/win32/api/windef/ns-windef-size) o objeto de `CSize` que especifica el número de unidades que se va a trasladar al valor devuelto.

*lpRect*<br/>
Apunta a una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` objeto que contiene el número de unidades que se va a deflatar cada lado del valor devuelto.

### <a name="return-value"></a>Valor devuelto

El `CRect` resultante de mover o desinflar `CRect` por el número de unidades especificadas en el parámetro.

### <a name="remarks"></a>Observaciones

Los parámetros *x* *e y* (o `cx` y `cy`) del parámetro se restan de la posición del `CRect`.

La tercera sobrecarga devuelve un nuevo `CRect` que es igual a `CRect` desinflado por el número de unidades especificado en cada miembro del parámetro. Tenga en cuenta que esta sobrecarga funciona como [DeflateRect](#deflaterect), no [SubtractRect](#subtractrect).

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect:: Operator &amp;

Devuelve un `CRect` que es la intersección de `CRect` y *rect2*.

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="return-value"></a>Valor devuelto

`CRect` que es la intersección de `CRect` y *rect2*.

### <a name="remarks"></a>Observaciones

La intersección es el rectángulo más grande que se encuentra en ambos rectángulos.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>CRect:: Operator&#124;

Devuelve un `CRect` que es la Unión de `CRect` y *rect2*.

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>Parámetros

*rect2*<br/>
Contiene un [rectángulo](/windows/win32/api/windef/ns-windef-rect) o un `CRect`.

### <a name="return-value"></a>Valor devuelto

`CRect` que es la Unión de `CRect` y *rect2*.

### <a name="remarks"></a>Observaciones

La Unión es el rectángulo más pequeño que contiene ambos rectángulos.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>CRect::P tInRect

Determina si el punto especificado se encuentra dentro de `CRect`.

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>Parámetros

*Elija*<br/>
Contiene una estructura de [punto](/windows/win32/api/windef/ns-windef-point) o un objeto [CPoint](cpoint-class.md) .

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el punto se encuentra dentro de `CRect`; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

Un punto está dentro de `CRect` si se encuentra en el lado izquierdo o superior o en los cuatro lados. Un punto del lado derecho o inferior está fuera de `CRect`.

> [!NOTE]
>  El rectángulo debe normalizarse o puede producirse un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

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

##  <a name="setrect"></a>CRect:: SetRect

Establece las dimensiones de `CRect` en las coordenadas especificadas.

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>Parámetros

*1*<br/>
Especifica la coordenada x de la esquina superior izquierda.

*y1*<br/>
Especifica la coordenada y de la esquina superior izquierda.

*RCA*<br/>
Especifica la coordenada x de la esquina inferior derecha.

*a2*<br/>
Especifica la coordenada y de la esquina inferior derecha.

### <a name="example"></a>Ejemplo

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect:: SetRectEmpty

Hace que `CRect` un rectángulo nulo estableciendo todas las coordenadas en cero.

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

##  <a name="size"></a>CRect:: SIZE

Los miembros `cx` y `cy` del valor devuelto contienen el alto y el ancho de `CRect`.

```
CSize Size() const throw();
```

### <a name="return-value"></a>Valor devuelto

Objeto [CSize](csize-class.md) que contiene el tamaño de `CRect`.

### <a name="remarks"></a>Observaciones

El alto o el ancho pueden ser negativos.

> [!NOTE]
>  El rectángulo debe normalizarse o puede producirse un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>CRect:: SubtractRect

Hace que las dimensiones de la `CRect` igual a la resta de `lpRectSrc2` de `lpRectSrc1`.

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRectSrc1*<br/>
Apunta a la estructura [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` objeto desde el que se va a restar un rectángulo.

*lpRectSrc2*<br/>
Apunta a la estructura `RECT` o `CRect` objeto que se va a restar del rectángulo señalado por el parámetro *lpRectSrc1* .

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si la función se realiza correctamente; de lo contrario, es 0.

### <a name="remarks"></a>Observaciones

La resta es el rectángulo más pequeño que contiene todos los puntos de *lpRectScr1* que no están en la intersección de *lpRectScr1* y *lpRectScr2*.

El rectángulo especificado por *lpRectSrc1* no se modificará si el rectángulo especificado por *lpRectSrc2* no se superpone completamente al rectángulo especificado por *lpRectSrc1* en al menos una de las direcciones x o y.

Por ejemplo, si *lpRectSrc1* eran (10, 10, 100.100) y *lpRectSrc2* eran (50, 50, 150.150), el rectángulo al que señala *lpRectSrc1* sería sin cambiar cuando se devolviera la función. Si *lpRectSrc1* eran (10, 10, 100.100) y *lpRectSrc2* eran (50, 10, 150.150), sin embargo, el rectángulo señalado por *lpRectSrc1* contendría las coordenadas (10, 10, 50.100) cuando se devolviera la función.

`SubtractRect` no es igual que [Operator-](#operator_-) ni [Operator-=](#operator_-_eq). Ninguno de estos operadores llama nunca `SubtractRect`.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

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

##  <a name="topleft"></a>CRect:: enleft

Las coordenadas se devuelven como una referencia a un objeto [CPoint](cpoint-class.md) contenido en `CRect`.

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>Valor devuelto

Coordenadas de la esquina superior izquierda del rectángulo.

### <a name="remarks"></a>Observaciones

Puede usar esta función para obtener o establecer la esquina superior izquierda del rectángulo. Establezca la esquina mediante esta función en el lado izquierdo del operador de asignación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CRect:: CenterPoint](#centerpoint).

##  <a name="unionrect"></a>CRect:: UnionRect

Hace que las dimensiones de `CRect` iguales a la Unión de los dos rectángulos de origen.

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>Parámetros

*lpRect1*<br/>
Apunta a un [Rect](/windows/win32/api/windef/ns-windef-rect) o `CRect` que contiene un rectángulo de origen.

*lpRect2*<br/>
Apunta a una `RECT` o `CRect` que contiene un rectángulo de origen.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la Unión no está vacía; 0 si la Unión está vacía.

### <a name="remarks"></a>Observaciones

La Unión es el rectángulo más pequeño que contiene ambos rectángulos de origen.

Windows omite las dimensiones de un rectángulo vacío; es decir, un rectángulo que no tiene ningún alto o que no tiene ancho.

> [!NOTE]
>  Ambos rectángulos se deben normalizar o se puede producir un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar los rectángulos antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect:: width

Calcula el ancho de `CRect` restando el valor izquierdo del valor derecho.

```
int Width() const throw();
```

### <a name="return-value"></a>Valor devuelto

Ancho de `CRect`.

### <a name="remarks"></a>Observaciones

El ancho puede ser negativo.

> [!NOTE]
>  El rectángulo debe normalizarse o puede producirse un error en esta función. Puede llamar a [NormalizeRect](#normalizerect) para normalizar el rectángulo antes de llamar a esta función.

### <a name="example"></a>Ejemplo

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>Consulte también

[CPoint (clase)](cpoint-class.md)<br/>
[CSize (clase)](csize-class.md)<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)
