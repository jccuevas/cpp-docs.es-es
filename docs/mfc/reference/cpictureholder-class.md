---
title: CPictureHolder (clase)
ms.date: 11/04/2016
f1_keywords:
- CPictureHolder
- AFXCTL/CPictureHolder
- AFXCTL/CPictureHolder::CPictureHolder
- AFXCTL/CPictureHolder::CreateEmpty
- AFXCTL/CPictureHolder::CreateFromBitmap
- AFXCTL/CPictureHolder::CreateFromIcon
- AFXCTL/CPictureHolder::CreateFromMetafile
- AFXCTL/CPictureHolder::GetDisplayString
- AFXCTL/CPictureHolder::GetPictureDispatch
- AFXCTL/CPictureHolder::GetType
- AFXCTL/CPictureHolder::Render
- AFXCTL/CPictureHolder::SetPictureDispatch
- AFXCTL/CPictureHolder::m_pPict
helpviewer_keywords:
- CPictureHolder [MFC], CPictureHolder
- CPictureHolder [MFC], CreateEmpty
- CPictureHolder [MFC], CreateFromBitmap
- CPictureHolder [MFC], CreateFromIcon
- CPictureHolder [MFC], CreateFromMetafile
- CPictureHolder [MFC], GetDisplayString
- CPictureHolder [MFC], GetPictureDispatch
- CPictureHolder [MFC], GetType
- CPictureHolder [MFC], Render
- CPictureHolder [MFC], SetPictureDispatch
- CPictureHolder [MFC], m_pPict
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
ms.openlocfilehash: 067ea7238c48f2698d7bfe469e9c4be10129c065
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364053"
---
# <a name="cpictureholder-class"></a>CPictureHolder (clase)

Implementa un Picture propiedad, que permite al usuario mostrar una imagen en el control.

## <a name="syntax"></a>Sintaxis

```
class CPictureHolder
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPictureHolder::CPictureHolder](#cpictureholder)|Construye un objeto `CPictureHolder`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPictureHolder::CreateEmpty](#createempty)|Crea un objeto `CPictureHolder` vacío.|
|[CPictureHolder::CreateFromBitmap](#createfrombitmap)|Crea `CPictureHolder` un objeto a partir de un mapa de bits.|
|[CPictureHolder::CreateFromIcon](#createfromicon)|Crea `CPictureHolder` un objeto a partir de un icono.|
|[CPictureHolder::CreateFromMetafile](#createfrommetafile)|Crea `CPictureHolder` un objeto a partir de un metarchivo.|
|[CPictureHolder::GetDisplayString](#getdisplaystring)|Recupera la cadena que se muestra en el explorador de propiedades de un contenedor de controles.|
|[CPictureHolder::GetPictureDispatch](#getpicturedispatch)|Devuelve `CPictureHolder` la interfaz del `IDispatch` objeto.|
|[CPictureHolder::GetType](#gettype)|Indica si `CPictureHolder` el objeto es un mapa de bits, un metarchivo o un icono.|
|[CPictureHolder::Render](#render)|Representa la imagen.|
|[CPictureHolder::SetPictureDispatch](#setpicturedispatch)|Establece `CPictureHolder` la interfaz del `IDispatch` objeto.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPictureHolder::m_pPict](#m_ppict)|Puntero a un objeto de imagen.|

## <a name="remarks"></a>Observaciones

`CPictureHolder`no tiene una clase base.

Con la propiedad Picture de stock, el desarrollador puede especificar un mapa de bits, un icono o un metarchivo para su visualización.

Para obtener información sobre cómo crear propiedades de imagen personalizadas, vea el artículo Controles ActiveX de [MFC: Uso de imágenes en un control ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CPictureHolder`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxctl.h

## <a name="cpictureholdercpictureholder"></a><a name="cpictureholder"></a>CPictureHolder::CPictureHolder

Construye un objeto `CPictureHolder`.

```
CPictureHolder();
```

## <a name="cpictureholdercreateempty"></a><a name="createempty"></a>CPictureHolder::CreateEmpty

Crea un `CPictureHolder` objeto vacío y `IPicture` lo conecta a una interfaz.

```
BOOL CreateEmpty();
```

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se crea correctamente; de lo contrario 0.

## <a name="cpictureholdercreatefrombitmap"></a><a name="createfrombitmap"></a>CPictureHolder::CreateFromBitmap

Utiliza un mapa de bits `CPictureHolder`para inicializar el objeto de imagen en un archivo .

```
BOOL CreateFromBitmap(
    UINT idResource);

BOOL CreateFromBitmap(
    CBitmap* pBitmap,
    CPalette* pPal = NULL,
    BOOL bTransferOwnership = TRUE);

BOOL CreateFromBitmap(
    HBITMAP hbm,
    HPALETTE hpal = NULL,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parámetros

*idResource*<br/>
ID de recurso de un recurso de mapa de bits.

*pBitmap*<br/>
Puntero a un [CBitmap](../../mfc/reference/cbitmap-class.md) objeto.

*Ppal*<br/>
Puntero a un [CPalette](../../mfc/reference/cpalette-class.md) objeto.

*bTransferOwnership*<br/>
Indica si el objeto de imagen tomará posesión de los objetos de mapa de bits y paleta.

*Hbm*<br/>
Controlar el mapa de `CPictureHolder` bits desde el que se crea el objeto.

*hpal*<br/>
Controle la paleta utilizada para representar el mapa de bits.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *bTransferOwnership* es TRUE, el autor de la llamada no debe usar el objeto de mapa de bits o paleta de ninguna manera después de que se devuelve esta llamada. Si *bTransferOwnership* es FALSE, el autor de la llamada es responsable de garantizar que los objetos de mapa de bits y paleta sigan siendo válidos durante la duración del objeto de imagen.

## <a name="cpictureholdercreatefromicon"></a><a name="createfromicon"></a>CPictureHolder::CreateFromIcon

Utiliza un icono para inicializar el `CPictureHolder`objeto de imagen en un archivo .

```
BOOL CreateFromIcon(
    UINT idResource);

BOOL CreateFromIcon(
    HICON hIcon,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parámetros

*idResource*<br/>
ID de recurso de un recurso de mapa de bits.

*hIcon*<br/>
Controlar el icono desde `CPictureHolder` el que se crea el objeto.

*bTransferOwnership*<br/>
Indica si el objeto de imagen tomará posesión del objeto icon.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *bTransferOwnership* es TRUE, el autor de la llamada no debe usar el objeto icon de ninguna manera después de que se devuelve esta llamada. Si *bTransferOwnership* es FALSE, el autor de la llamada es responsable de asegurarse de que el objeto de icono sigue siendo válido durante la duración del objeto de imagen.

## <a name="cpictureholdercreatefrommetafile"></a><a name="createfrommetafile"></a>CPictureHolder::CreateFromMetafile

Utiliza un metarchivo para inicializar `CPictureHolder`el objeto de imagen en un archivo .

```
BOOL CreateFromMetafile(
    HMETAFILE hmf,
    int xExt,
    int yExt,
    BOOL bTransferOwnership = FALSE);
```

### <a name="parameters"></a>Parámetros

*Hmf*<br/>
Controlar el metarchivo utilizado `CPictureHolder` para crear el objeto.

*xExt*<br/>
X extensión de la imagen.

*yExt*<br/>
Y extensión de la imagen.

*bTransferOwnership*<br/>
Indica si el objeto de imagen tomará la propiedad del objeto de metarchivo.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si el objeto se crea correctamente; de lo contrario 0.

### <a name="remarks"></a>Observaciones

Si *bTransferOwnership* es TRUE, el llamador no debe usar el objeto de metarchivo de ninguna manera después de que se devuelve esta llamada. Si *bTransferOwnership* es FALSE, el autor de la llamada es responsable de asegurarse de que el objeto de metarchivo sigue siendo válido durante la duración del objeto de imagen.

## <a name="cpictureholdergetdisplaystring"></a><a name="getdisplaystring"></a>CPictureHolder::GetDisplayString

Recupera la cadena que se muestra en el explorador de propiedades de un contenedor.

```
BOOL GetDisplayString(CString& strValue);
```

### <a name="parameters"></a>Parámetros

*strValue*<br/>
Referencia a la [CString](../../atl-mfc-shared/reference/cstringt-class.md) que va a contener la cadena de presentación.

### <a name="return-value"></a>Valor devuelto

Distinto de cero si la cadena se recupera correctamente; de lo contrario 0.

## <a name="cpictureholdergetpicturedispatch"></a><a name="getpicturedispatch"></a>CPictureHolder::GetPictureDispatch

Esta función devuelve `CPictureHolder` un puntero `IPictureDisp` a la interfaz del objeto.

```
LPPICTUREDISP GetPictureDispatch();
```

### <a name="return-value"></a>Valor devuelto

Un puntero `CPictureHolder` a la `IPictureDisp` interfaz del objeto.

### <a name="remarks"></a>Observaciones

El llamador `Release` debe llamar a este puntero cuando haya terminado con él.

## <a name="cpictureholdergettype"></a><a name="gettype"></a>CPictureHolder::GetType

Indica si la imagen es un mapa de bits, un metarchivo o un icono.

```
short GetType();
```

### <a name="return-value"></a>Valor devuelto

Valor que indica el tipo de la imagen. Los valores posibles y sus significados son los siguientes:

|Value|Significado|
|-----------|-------------|
|PICTYPE_UNINITIALIZED|`CPictureHolder`objeto se unializa.|
|PICTYPE_NONE|`CPictureHolder`objeto está vacío.|
|PICTYPE_BITMAP|Picture es un mapa de bits.|
|PICTYPE_METAFILE|Picture es un metarchivo.|
|PICTYPE_ICON|La imagen es un icono.|

## <a name="cpictureholderm_ppict"></a><a name="m_ppict"></a>CPictureHolder::m_pPict

Un puntero `CPictureHolder` a la `IPicture` interfaz del objeto.

```
LPPICTURE m_pPict;
```

## <a name="cpictureholderrender"></a><a name="render"></a>CPictureHolder::Render

Representa la imagen en el rectángulo al que hace referencia *rcRender*.

```
void Render(
    CDC* pDC,
    const CRect& rcRender,
    const CRect& rcWBounds);
```

### <a name="parameters"></a>Parámetros

*pDC*<br/>
Puntero al contexto de visualización en el que se va a representar la imagen.

*rcRender*<br/>
Rectángulo en el que se va a representar la imagen.

*rcWBounds*<br/>
Rectángulo que representa el rectángulo delimitador del objeto que representa la imagen. Para un control, este rectángulo es el *rcBounds* parámetro pasado a una invalidación de [COleControl::OnDraw](../../mfc/reference/colecontrol-class.md#ondraw).

## <a name="cpictureholdersetpicturedispatch"></a><a name="setpicturedispatch"></a>CPictureHolder::SetPictureDispatch

Conecta `CPictureHolder` el objeto `IPictureDisp` a una interfaz.

```
void SetPictureDispatch(LPPICTUREDISP pDisp);
```

### <a name="parameters"></a>Parámetros

*pDisp*<br/>
Puntero a `IPictureDisp` la nueva interfaz.

## <a name="see-also"></a>Consulte también

[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CFontHolder (clase)](../../mfc/reference/cfontholder-class.md)
