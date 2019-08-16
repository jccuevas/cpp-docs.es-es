---
title: Clase CFontHolder
ms.date: 11/04/2016
f1_keywords:
- CFontHolder
- AFXCTL/CFontHolder
- AFXCTL/CFontHolder::CFontHolder
- AFXCTL/CFontHolder::GetDisplayString
- AFXCTL/CFontHolder::GetFontDispatch
- AFXCTL/CFontHolder::GetFontHandle
- AFXCTL/CFontHolder::InitializeFont
- AFXCTL/CFontHolder::QueryTextMetrics
- AFXCTL/CFontHolder::ReleaseFont
- AFXCTL/CFontHolder::Select
- AFXCTL/CFontHolder::SetFont
- AFXCTL/CFontHolder::m_pFont
helpviewer_keywords:
- CFontHolder [MFC], CFontHolder
- CFontHolder [MFC], GetDisplayString
- CFontHolder [MFC], GetFontDispatch
- CFontHolder [MFC], GetFontHandle
- CFontHolder [MFC], InitializeFont
- CFontHolder [MFC], QueryTextMetrics
- CFontHolder [MFC], ReleaseFont
- CFontHolder [MFC], Select
- CFontHolder [MFC], SetFont
- CFontHolder [MFC], m_pFont
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
ms.openlocfilehash: 04de8141469f82bdd1fbb6adc1bae94d6026324c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506444"
---
# <a name="cfontholder-class"></a>Clase CFontHolder

Implementa la propiedad Font estándar y encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz de `IFont` .

## <a name="syntax"></a>Sintaxis

```
class CFontHolder
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Construye un objeto `CFontHolder`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena mostrada en el explorador de propiedades de un contenedor.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Devuelve la interfaz de `IDispatch` la fuente.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Devuelve un identificador para una fuente de Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Inicializa un `CFontHolder` objeto.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Recupera información de la fuente relacionada.|
|[CFontHolder::ReleaseFont](#releasefont)|Desconecta el `CFontHolder` objeto de las `IFont` interfaces y `IFontNotification` .|
|[CFontHolder::Select](#select)|Selecciona un recurso de fuente en un contexto de dispositivo.|
|[CFontHolder::SetFont](#setfont)|Conecta el `CFontHolder` objeto a una `IFont` interfaz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Puntero a la `CFontHolder` interfaz del `IFont` objeto.|

## <a name="remarks"></a>Comentarios

`CFontHolder`no tiene una clase base.

Utilice esta clase para implementar propiedades de fuente personalizadas para el control. Para obtener información sobre cómo crear estas propiedades, vea [el artículo controles ActiveX: Usar fuentes](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CFontHolder`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl. h

##  <a name="cfontholder"></a>  CFontHolder::CFontHolder

Construye un objeto `CFontHolder`.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parámetros

*pNotify*<br/>
Puntero a la interfaz de `IPropertyNotifySink` la fuente.

### <a name="remarks"></a>Comentarios

Debe llamar `InitializeFont` a para inicializar el objeto resultante antes de usarlo.

##  <a name="getdisplaystring"></a>  CFontHolder::GetDisplayString

Recupera una cadena que se puede mostrar en el explorador de propiedades de un contenedor.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parámetros

*strValue*<br/>
Referencia al [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena se recupera correctamente; de lo contrario, es 0.

##  <a name="getfontdispatch"></a>  CFontHolder::GetFontDispatch

Llame a esta función para recuperar un puntero a la interfaz de envío de la fuente.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Valor devuelto

Puntero a la `CFontHolder` interfaz del `IFontDisp` objeto. Tenga en cuenta que la función `GetFontDispatch` a la `IUnknown::Release` que llama debe llamar a en este puntero de interfaz cuando se hace con él.

### <a name="remarks"></a>Comentarios

Llame `InitializeFont` a antes `GetFontDispatch`de llamar a.

##  <a name="getfonthandle"></a>  CFontHolder::GetFontHandle

Llame a esta función para obtener un identificador de una fuente de Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parámetros

*cyLogical*<br/>
Alto, en unidades lógicas, del rectángulo en el que se dibuja el control.

*cyHimetric*<br/>
Alto, en unidades MM_HIMETRIC, del control.

### <a name="return-value"></a>Valor devuelto

Identificador del objeto de fuente; de lo contrario, NULL.

### <a name="remarks"></a>Comentarios

La proporción de *cyLogical* y *cyHimetric* se usa para calcular el tamaño de presentación adecuado, en unidades lógicas, para el tamaño de punto de la fuente expresado en unidades de MM_HIMETRIC:

Display size = ( *cyLogical* / *cyHimetric*) X tamaño de fuente

La versión sin parámetros devuelve un identificador a un tamaño de fuente correctamente para la pantalla.

##  <a name="initializefont"></a>  CFontHolder::InitializeFont

Inicializa un `CFontHolder` objeto.

```
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parámetros

*pFontDesc*<br/>
Puntero a una estructura de descripción de fuente ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) que especifica las características de la fuente.

*pFontDispAmbient*<br/>
Puntero a la propiedad de fuente ambiente del contenedor.

### <a name="remarks"></a>Comentarios

Si *pFontDispAmbient* no es null, el `CFontHolder` objeto se conecta a un clon de la `IFont` interfaz utilizada por la propiedad de fuente ambiente del contenedor.

Si *pFontDispAmbient* es null, se crea un nuevo objeto de fuente a partir de la descripción de fuente a la que apunta *pFontDesc* o, si *pFontDesc* es null, de una descripción predeterminada.

Llame a esta función después de construir `CFontHolder` un objeto.

##  <a name="m_pfont"></a>  CFontHolder::m_pFont

Puntero a la `CFontHolder` interfaz del `IFont` objeto.

```
LPFONT m_pFont;
```

##  <a name="querytextmetrics"></a>  CFontHolder::QueryTextMetrics

Recupera información sobre la fuente física representada por `CFontHolder` el objeto.

```
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parámetros

*lptm*<br/>
Puntero a una estructura [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) que recibirá la información.

##  <a name="releasefont"></a>  CFontHolder::ReleaseFont

Esta función desconecta el `CFontHolder` objeto de su `IFont` interfaz.

```
void ReleaseFont();
```

##  <a name="select"></a>  CFontHolder::Select

Llame a esta función para seleccionar la fuente del control en el contexto de dispositivo especificado.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Contexto de dispositivo en el que se selecciona la fuente.

*cyLogical*<br/>
Alto, en unidades lógicas, del rectángulo en el que se dibuja el control.

*cyHimetric*<br/>
Alto, en unidades MM_HIMETRIC, del control.

### <a name="return-value"></a>Valor devuelto

Puntero a la fuente que se va a reemplazar.

### <a name="remarks"></a>Comentarios

Consulte [GetFontHandle](#getfonthandle) para obtener una explicación de los parámetros *cyLogical* y *cyHimetric* .

##  <a name="setfont"></a>  CFontHolder::SetFont

Libera cualquier fuente existente y conecta el `CFontHolder` objeto a una `IFont` interfaz.

```
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parámetros

*pNewFont*<br/>
Puntero a la nueva `IFont` interfaz.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CPropExchange (clase)](../../mfc/reference/cpropexchange-class.md)
