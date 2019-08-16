---
title: CAnimateCtrl (clase)
ms.date: 11/04/2016
f1_keywords:
- CAnimateCtrl
- AFXCMN/CAnimateCtrl
- AFXCMN/CAnimateCtrl::CAnimateCtrl
- AFXCMN/CAnimateCtrl::Close
- AFXCMN/CAnimateCtrl::Create
- AFXCMN/CAnimateCtrl::CreateEx
- AFXCMN/CAnimateCtrl::IsPlaying
- AFXCMN/CAnimateCtrl::Open
- AFXCMN/CAnimateCtrl::Play
- AFXCMN/CAnimateCtrl::Seek
- AFXCMN/CAnimateCtrl::Stop
helpviewer_keywords:
- CAnimateCtrl [MFC], CAnimateCtrl
- CAnimateCtrl [MFC], Close
- CAnimateCtrl [MFC], Create
- CAnimateCtrl [MFC], CreateEx
- CAnimateCtrl [MFC], IsPlaying
- CAnimateCtrl [MFC], Open
- CAnimateCtrl [MFC], Play
- CAnimateCtrl [MFC], Seek
- CAnimateCtrl [MFC], Stop
ms.assetid: 5e8eb1bd-96b7-47b8-8de2-6bcbb3cc299b
ms.openlocfilehash: adf8302508b81f1ac4f6cce3e3811ea6e3743bd4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507689"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl (clase)

Proporciona la funcionalidad del control común de animación de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construye un objeto `CAnimateCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CAnimateCtrl::Close](#close)|Cierra el clip AVI.|
|[CAnimateCtrl::Create](#create)|Crea un control Animation y lo adjunta a un `CAnimateCtrl` objeto.|
|[CAnimateCtrl::CreateEx](#createex)|Crea un control de animación con los estilos extendidos de Windows especificados y lo `CAnimateCtrl` adjunta a un objeto.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Indica si se está reproduciendo un clip de audio y vídeo intercalado (AVI).|
|[CAnimateCtrl::Open](#open)|Abre un clip AVI desde un archivo o recurso y muestra el primer fotograma.|
|[CAnimateCtrl::Play](#play)|Reproduce el clip AVI sin sonido.|
|[CAnimateCtrl::Seek](#seek)|Muestra un solo fotograma seleccionado del clip AVI.|
|[CAnimateCtrl::Stop](#stop)|Detiene la reproducción del clip AVI.|

## <a name="remarks"></a>Comentarios

Este control (y, por `CAnimateCtrl` lo tanto, la clase) solo está disponible para programas que se ejecutan en Windows 95, Windows 98 y Windows NT versión 3,51 y versiones posteriores.

Un control de animación es una ventana rectangular que muestra un clip en formato AVI (audio de vídeo intercalado), el formato de vídeo/audio estándar de Windows. Un clip AVI es una serie de fotogramas de mapa de bits, como una película.

Los controles de animación solo pueden reproducir clips AVI sencillos. En concreto, los clips que va a reproducir un control Animation deben cumplir los siguientes requisitos:

- Debe haber exactamente un flujo de vídeo y debe tener al menos un fotograma.

- Puede haber como máximo dos flujos en el archivo (normalmente, la otra secuencia, si está presente, es una secuencia de audio, aunque el control de animación omite la información de audio).

- El clip debe descomprimirse o comprimirse con la compresión RLE8.

- No se permiten cambios de paleta en el flujo de vídeo.

Puede Agregar el clip AVI a la aplicación como un recurso AVI o puede acompañar a la aplicación como un archivo AVI independiente.

Dado que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común de un control de animación es indicar la actividad del sistema durante una operación larga. Por ejemplo, el cuadro de diálogo Buscar del explorador de archivos muestra una lupa en movimiento mientras el sistema busca un archivo.

Si crea un `CAnimateCtrl` objeto dentro de un cuadro de diálogo o de un recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, se destruirá automáticamente cuando el usuario cierre el cuadro de diálogo.

Si crea un `CAnimateCtrl` objeto dentro de una ventana, puede que tenga que destruirlo. Si crea el `CAnimateCtrl` objeto en la pila, se destruye automáticamente. Si crea el `CAnimateCtrl` objeto en el montón mediante la **nueva** función, debe llamar a **Delete** en el objeto para destruirlo. Si deriva una nueva clase de `CAnimateCtrl` y asigna cualquier memoria en esa clase, invalide el `CAnimateCtrl` destructor para desechar las asignaciones.

Para obtener más información sobre `CAnimateCtrl`el uso de, vea [controles](../../mfc/controls-mfc.md) y [usar CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

##  <a name="canimatectrl"></a>  CAnimateCtrl::CAnimateCtrl

Construye un objeto `CAnimateCtrl`.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Comentarios

Debe llamar a la función miembro [Create](#create) para poder realizar cualquier otra operación en el objeto que cree.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

##  <a name="close"></a>  CAnimateCtrl::Close

Cierra el clip AVI que se abrió previamente en el control de animación (si existe) y lo quita de la memoria.

```
BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

##  <a name="create"></a>  CAnimateCtrl::Create

Crea un control Animation y lo adjunta a un `CAnimateCtrl` objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de animación. Aplique cualquier combinación de los estilos de Windows que se describen en la sección comentarios que aparece a continuación y los estilos de control de animación descritos en [estilos de control de animación](/windows/win32/Controls/animation-control-styles) en el Windows SDK.

*rect*<br/>
Especifica la posición y el tamaño del control de animación. Puede ser un objeto [CRect](../../atl-mfc-shared/reference/crect-class.md) o una estructura [Rect](/windows/win32/api/windef/ns-windef-rect) .

*pParentWnd*<br/>
Especifica la ventana primaria del control de animación, normalmente `CDialog`una. No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de animación.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

En dos pasos `CAnimateCtrl` se crea un. En primer lugar, llame al constructor y, `Create`a continuación, llame a, que crea el control Animation y `CAnimateCtrl` lo adjunta al objeto.

Aplique los siguientes [estilos de ventana](../../mfc/reference/styles-used-by-mfc.md#window-styles) a un control de animación.

- WS_CHILD siempre

- WS_VISIBLE normalmente

- WS_DISABLED raramente

Si desea utilizar estilos extendidos de Windows con el control de animación, llame a [CreateEx](#createex) en `Create`lugar de a.

Además de los estilos de ventana enumerados anteriormente, es posible que desee aplicar uno o varios estilos de control de animación a un control de animación. Vea el Windows SDK para obtener más información sobre los [estilos de control de animación](/windows/win32/Controls/animation-control-styles).

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

##  <a name="createex"></a>  CAnimateCtrl::CreateEx

Crea un control (una ventana secundaria) y lo asocia al `CAnimateCtrl` objeto.

```
virtual BOOL CreateEx(
    DWORD dwExStyle,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwExStyle*<br/>
Especifica el estilo extendido del control que se va a crear. Para obtener una lista de los estilos extendidos de Windows, consulte el parámetro *dwExStyle* para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de animación. Aplique cualquier combinación de los estilos de control de animación y ventana descritos en [estilos de control de animación](/windows/win32/Controls/animation-control-styles) en el Windows SDK.

*rect*<br/>
Referencia a una estructura [Rect](/previous-versions/dd162897\(v=vs.85\)) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
IDENTIFICADOR de la ventana de elemento secundario del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Use `CreateEx` en lugar de [crear](#create) para aplicar los estilos extendidos de Windows, que especifica el **WS_EX_** de estilo extendido de Windows.

##  <a name="isplaying"></a>  CAnimateCtrl::IsPlaying

Indica si se está reproduciendo un clip de audio y vídeo intercalado (AVI).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Valor devuelto

TRUE si se está reproduciendo un clip AVI; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Este método envía el mensaje [ACM_ISPLAYING](/windows/win32/Controls/acm-isplaying) , que se describe en el Windows SDK.

##  <a name="open"></a>  CAnimateCtrl::Open

Llame a esta función para abrir un clip AVI y mostrar su primer fotograma.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Un `CString` objeto o un puntero a una cadena terminada en null que contiene el nombre del archivo AVI o el nombre de un recurso AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se abrió previamente para el control de animación, si existe.

*nID*<br/>
Identificador de recursos AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se abrió previamente para el control de animación, si existe.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El recurso AVI se carga desde el módulo que creó el control Animation.

`Open`no admite sonido en un clip AVI; solo puede abrir clips AVI silenciosos.

Si el control de animación tiene `ACS_AUTOPLAY` el estilo, el control de animación comenzará a reproducir automáticamente el clip inmediatamente después de que se abra. Continuará reproduciendo el clip en segundo plano mientras se sigue ejecutando el subproceso. Cuando el clip haya terminado de reproducirse, se repetirá automáticamente.

Si el control de animación tiene `ACS_CENTER` el estilo, el clip AVI se centrará en el control y el tamaño del control no cambiará. Si el control de animación no tiene el `ACS_CENTER` estilo, se cambiará el tamaño del control cuando se abra el clip AVI hasta el tamaño de las imágenes del clip AVI. La posición de la esquina superior izquierda del control no cambia, solo el tamaño del control.

Si el control de animación tiene `ACS_TRANSPARENT` el estilo, el primer fotograma se dibujará con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

##  <a name="play"></a>CAnimateCtrl::P establecer

Llame a esta función para reproducir un clip AVI en un control Animation.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parámetros

*nFrom*<br/>
Índice de base cero del marco en el que comienza la reproducción. El valor debe ser inferior a 65.536. Un valor de 0 significa comenzar con el primer fotograma del clip AVI.

*nTo*<br/>
Índice de base cero del marco en el que finaliza la reproducción. El valor debe ser inferior a 65.536. Un valor de-1 significa terminar con el último fotograma del clip AVI.

*nRep*<br/>
Número de veces que se va a reproducir el clip AVI. Un valor de-1 significa reproducir el archivo indefinidamente.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

El control de animación reproducirá el clip en segundo plano mientras se sigue ejecutando el subproceso. Si el control de animación `ACS_TRANSPARENT` tiene estilo, el clip AVI se reproducirá con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

##  <a name="seek"></a>  CAnimateCtrl::Seek

Llame a esta función para mostrar estáticamente un solo fotograma del clip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parámetros

*nTo*<br/>
Índice de base cero del marco que se va a mostrar. El valor debe ser inferior a 65.536. Un valor de 0 significa mostrar el primer fotograma del clip AVI. Un valor de-1 significa mostrar el último fotograma del clip AVI.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Comentarios

Si el control de animación `ACS_TRANSPARENT` tiene estilo, el clip AVI se dibujará con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

##  <a name="stop"></a>  CAnimateCtrl::Stop

Llame a esta función para detener la reproducción de un clip AVI en un control Animation.

```
BOOL Stop();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl:: CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
