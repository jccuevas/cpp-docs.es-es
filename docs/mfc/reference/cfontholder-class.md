---
title: CFontHolder (clase)
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
ms.openlocfilehash: 36fbebc39101c5534bd52d4f79fee5286487a6e0
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81754985"
---
# <a name="cfontholder-class"></a>CFontHolder (clase)

Implementa la propiedad Font estándar y encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz de `IFont` .

## <a name="syntax"></a>Sintaxis

```
class CFontHolder
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontHolder::CFontHolder](#cfontholder)|Construye un objeto `CFontHolder`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena que se muestra en el explorador de propiedades de un contenedor.|
|[CFontHolder::GetFontDispatch](#getfontdispatch)|Devuelve la interfaz de la `IDispatch` fuente.|
|[CFontHolder::GetFontHandle](#getfonthandle)|Devuelve un identificador a una fuente de Windows.|
|[CFontHolder::InitializeFont](#initializefont)|Inicializa un objeto `CFontHolder`.|
|[CFontHolder::QueryTextMetrics](#querytextmetrics)|Recupera información para la fuente relacionada.|
|[CFontHolder::ReleaseFont](#releasefont)|Desconecta `CFontHolder` el `IFont` objeto `IFontNotification` de las interfaces y.|
|[CFontHolder::Select](#select)|Selecciona un recurso de fuente en un contexto de dispositivo.|
|[CFontHolder::SetFont](#setfont)|Conecta `CFontHolder` el objeto `IFont` a una interfaz.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CFontHolder::m_pFont](#m_pfont)|Un puntero `CFontHolder` a la `IFont` interfaz del objeto.|

## <a name="remarks"></a>Observaciones

`CFontHolder`no tiene una clase base.

Utilice esta clase para implementar propiedades de fuente personalizadas para el control. Para obtener información sobre cómo crear estas propiedades, consulte el artículo [Controles ActiveX: Uso de fuentes](../../mfc/mfc-activex-controls-using-fonts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CFontHolder`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="cfontholdercfontholder"></a><a name="cfontholder"></a>CFontHolder::CFontHolder

Construye un objeto `CFontHolder`.

```
explicit CFontHolder(LPPROPERTYNOTIFYSINK pNotify);
```

### <a name="parameters"></a>Parámetros

*pNotificar*<br/>
Puntero a la `IPropertyNotifySink` interfaz de la fuente.

### <a name="remarks"></a>Observaciones

Debe llamar `InitializeFont` para inicializar el objeto resultante antes de usarlo.

## <a name="cfontholdergetdisplaystring"></a><a name="getdisplaystring"></a>CFontHolder::GetDisplayString

Recupera una cadena que se puede mostrar en el explorador de propiedades de un contenedor.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parámetros

*strValue*<br/>
Referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena se recupera correctamente; de lo contrario 0.

## <a name="cfontholdergetfontdispatch"></a><a name="getfontdispatch"></a>CFontHolder::GetFontDispatch

Llame a esta función para recuperar un puntero a la interfaz de envío de la fuente.

```
LPFONTDISP GetFontDispatch();
```

### <a name="return-value"></a>Valor devuelto

Un puntero `CFontHolder` a la `IFontDisp` interfaz del objeto. Tenga en cuenta `GetFontDispatch` que `IUnknown::Release` la función que llama debe llamar a este puntero de interfaz cuando se hace con él.

### <a name="remarks"></a>Observaciones

Llame `InitializeFont` antes `GetFontDispatch`de llamar a .

## <a name="cfontholdergetfonthandle"></a><a name="getfonthandle"></a>CFontHolder::GetFontHandle

Llame a esta función para obtener un identificador de una fuente de Windows.

```
HFONT GetFontHandle();

HFONT GetFontHandle(
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parámetros

*cyLogical*<br/>
Altura, en unidades lógicas, del rectángulo en el que se dibuja el control.

*cyHimetric*<br/>
Altura, en unidades MM_HIMETRIC, del control.

### <a name="return-value"></a>Valor devuelto

Un identificador para el Font objeto; NULL.

### <a name="remarks"></a>Observaciones

La relación de *cyLogical* y *cyHimetric* se utiliza para calcular el tamaño de visualización adecuado, en unidades lógicas, para el tamaño de punto de la fuente expresado en MM_HIMETRIC unidades:

Tamaño de la pantalla ( *cyLogical* / *cyHimetric*) X tamaño de fuente

La versión sin parámetros devuelve un identificador a una fuente con el tamaño correcto para la pantalla.

## <a name="cfontholderinitializefont"></a><a name="initializefont"></a>CFontHolder::InitializeFont

Inicializa un objeto `CFontHolder`.

```cpp
void InitializeFont(
    const FONTDESC* pFontDesc = NULL,
    LPDISPATCH pFontDispAmbient = NULL);
```

### <a name="parameters"></a>Parámetros

*pFontDesc*<br/>
Puntero a una estructura de descripción de fuente ( [FONTDESC](/windows/win32/api/olectl/ns-olectl-fontdesc)) que especifica las características de la fuente.

*pFontDispAmbient*<br/>
Puntero a la propiedad Font ambiente del contenedor.

### <a name="remarks"></a>Observaciones

Si *pFontDispAmbient* no es `CFontHolder` NULL, el objeto `IFont` está conectado a un clon de la interfaz utilizada por la propiedad Font ambiental del contenedor.

Si *pFontDispAmbient* es NULL, se crea un nuevo objeto Font a partir de la descripción de fuente señalada por *pFontDesc* o, si *pFontDesc* es NULL, a partir de una descripción predeterminada.

Llame a esta función después de construir un `CFontHolder` objeto.

## <a name="cfontholderm_pfont"></a><a name="m_pfont"></a>CFontHolder::m_pFont

Un puntero `CFontHolder` a la `IFont` interfaz del objeto.

```
LPFONT m_pFont;
```

## <a name="cfontholderquerytextmetrics"></a><a name="querytextmetrics"></a>CFontHolder::QueryTextMetrics

Recupera información sobre la fuente física `CFontHolder` representada por el objeto.

```cpp
void QueryTextMetrics(LPTEXTMETRIC lptm);
```

### <a name="parameters"></a>Parámetros

*lptm*<br/>
Puntero a una estructura [TEXTMETRIC](/windows/win32/api/wingdi/ns-wingdi-textmetricw) que recibirá la información.

## <a name="cfontholderreleasefont"></a><a name="releasefont"></a>CFontHolder::ReleaseFont

Esta función `CFontHolder` desconecta `IFont` el objeto de su interfaz.

```cpp
void ReleaseFont();
```

## <a name="cfontholderselect"></a><a name="select"></a>CFontHolder::Select

Llame a esta función para seleccionar la fuente del control en el contexto de dispositivo especificado.

```
CFont* Select(
    CDC* pDC,
    long cyLogical,
    long cyHimetric);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Contexto del dispositivo en el que se selecciona la fuente.

*cyLogical*<br/>
Altura, en unidades lógicas, del rectángulo en el que se dibuja el control.

*cyHimetric*<br/>
Altura, en unidades MM_HIMETRIC, del control.

### <a name="return-value"></a>Valor devuelto

Un puntero a la fuente que se va a reemplazar.

### <a name="remarks"></a>Observaciones

Consulte [GetFontHandle](#getfonthandle) para obtener una explicación de los parámetros *cyLogical* y *cyHimetric.*

## <a name="cfontholdersetfont"></a><a name="setfont"></a>CFontHolder::SetFont

Libera cualquier fuente existente `CFontHolder` y `IFont` conecta el objeto a una interfaz.

```cpp
void SetFont(LPFONT pNewFont);
```

### <a name="parameters"></a>Parámetros

*pNewFont*<br/>
Puntero a `IFont` la nueva interfaz.

## <a name="see-also"></a>Vea también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CPropExchange](../../mfc/reference/cpropexchange-class.md)
