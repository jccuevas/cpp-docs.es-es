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
ms.openlocfilehash: e570681c899d58e8659635d55da843c23d1e95ee
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81752886"
---
# <a name="canimatectrl-class"></a>CAnimateCtrl (clase)

Proporciona la funcionalidad del control común de animación de Windows.

## <a name="syntax"></a>Sintaxis

```
class CAnimateCtrl : public CWnd
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimateCtrl::CAnimateCtrl](#canimatectrl)|Construye un objeto `CAnimateCtrl`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAnimateCtrl::Cerrar](#close)|Cierra el clip AVI.|
|[CAnimateCtrl::Create](#create)|Crea un control de animación `CAnimateCtrl` y lo asocia a un objeto.|
|[CAnimateCtrl::CreateEx](#createex)|Crea un control de animación con los estilos `CAnimateCtrl` extendidos de Windows especificados y lo asocia a un objeto.|
|[CAnimateCtrl::IsPlaying](#isplaying)|Indica si se está reproduciendo un clip entrelazado de audio y vídeo (AVI).|
|[CAnimateCtrl::Abrir](#open)|Abre un clip AVI desde un archivo o recurso y muestra el primer fotograma.|
|[CAnimateCtrl::Play](#play)|Reproduce el clip AVI sin sonido.|
|[CAnimateCtrl::Buscar](#seek)|Muestra un solo fotograma seleccionado del clip AVI.|
|[CAnimateCtrl::Stop](#stop)|Detiene la reproducción del clip AVI.|

## <a name="remarks"></a>Observaciones

Este control (y, por lo tanto, la `CAnimateCtrl` clase) solo está disponible para programas que se ejecutan en Windows 95, Windows 98 y Windows NT versión 3.51 y versiones posteriores.

Un control de animación es una ventana rectangular que muestra un clip en formato AVI (Audio Video Interleaved), el formato estándar de vídeo/audio de Windows. Un clip AVI es una serie de fotogramas de mapa de bits, como una película.

Los controles de animación solo pueden reproducir clips AVI simples. En concreto, los clips que va a reproducir un control de animación deben cumplir los siguientes requisitos:

- Debe haber exactamente una secuencia de vídeo y debe tener al menos un fotograma.

- Puede haber como máximo dos secuencias en el archivo (normalmente la otra secuencia, si está presente, es una secuencia de audio, aunque el control de animación omite la información de audio).

- El clip debe estar descomprimido o comprimido con compresión RLE8.

- No se permiten cambios en la paleta en la secuencia de vídeo.

Puede agregar el clip AVI a su aplicación como un recurso AVI, o puede acompañar su aplicación como un archivo AVI separado.

Dado que el subproceso continúa ejecutándose mientras se muestra el clip AVI, un uso común para un control de animación es indicar la actividad del sistema durante una operación prolongada. Por ejemplo, el cuadro de diálogo Buscar del Explorador de archivos muestra una lupa en movimiento mientras el sistema busca un archivo.

Si crea `CAnimateCtrl` un objeto dentro de un cuadro de diálogo o desde un recurso de cuadro de diálogo mediante el editor de cuadros de diálogo, se destruirá automáticamente cuando el usuario cierre el cuadro de diálogo.

Si crea `CAnimateCtrl` un objeto dentro de una ventana, es posible que deba destruirlo. Si crea `CAnimateCtrl` el objeto en la pila, se destruye automáticamente. Si crea `CAnimateCtrl` el objeto en el montón mediante la **nueva** función, debe llamar a **delete** en el objeto para destruirlo. Si deriva una nueva `CAnimateCtrl` clase de y asigna cualquier `CAnimateCtrl` memoria de esa clase, reemplace el destructor para eliminar las asignaciones.

Para obtener más `CAnimateCtrl`información sobre el uso de , vea [Controles](../../mfc/controls-mfc.md) y uso de [CAnimateCtrl](../../mfc/using-canimatectrl.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CAnimateCtrl`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxcmn.h

## <a name="canimatectrlcanimatectrl"></a><a name="canimatectrl"></a>CAnimateCtrl::CAnimateCtrl

Construye un objeto `CAnimateCtrl`.

```
CAnimateCtrl();
```

### <a name="remarks"></a>Observaciones

Debe llamar a la [create](#create) función miembro antes de poder realizar cualquier otra operación en el objeto que cree.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCControlLadenDialog#56](../../mfc/codesnippet/cpp/canimatectrl-class_1.cpp)]

## <a name="canimatectrlclose"></a><a name="close"></a>CAnimateCtrl::Cerrar

Cierra el clip AVI que se abrió anteriormente en el control de animación (si existe) y lo quita de la memoria.

```
BOOL Close();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreate"></a><a name="create"></a>CAnimateCtrl::Create

Crea un control de animación `CAnimateCtrl` y lo asocia a un objeto.

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>Parámetros

*dwStyle*<br/>
Especifica el estilo del control de animación. Aplique cualquier combinación de los estilos de windows descritos en la sección Comentarios a continuación y los estilos de control de animación descritos en [Estilos](/windows/win32/Controls/animation-control-styles) de control de animación en el Windows SDK.

*Rect*<br/>
Especifica la posición y el tamaño del control de animación. Puede ser un [CRect](../../atl-mfc-shared/reference/crect-class.md) objeto o un [RECT](/windows/win32/api/windef/ns-windef-rect) estructura.

*pParentWnd*<br/>
Especifica la ventana primaria del control `CDialog`de animación, normalmente un archivo . No debe ser NULL.

*nID*<br/>
Especifica el identificador del control de animación.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se construye `CAnimateCtrl` un en dos pasos. En primer lugar, llame `Create`al constructor y, a continuación, `CAnimateCtrl` llame a , que crea el control de animación y lo adjunta al objeto.

Aplique los siguientes [estilos](../../mfc/reference/styles-used-by-mfc.md#window-styles) de ventana a un control de animación.

- WS_CHILD Siempre

- WS_VISIBLE Por lo general

- WS_DISABLED Rara vez

Si desea utilizar estilos de ventanas extendidas con `Create`el control de animación, llame a [CreateEx](#createex) en lugar de .

Además de los estilos de ventana enumerados anteriormente, es posible que desee aplicar uno o varios de los estilos de control de animación a un control de animación. Consulte el Windows SDK para obtener más información sobre los estilos de control de [animación.](/windows/win32/Controls/animation-control-styles)

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlcreateex"></a><a name="createex"></a>CAnimateCtrl::CreateEx

Crea un control (una ventana secundaria) `CAnimateCtrl` y lo asocia con el objeto.

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
Especifica el estilo extendido del control que se está creando. Para obtener una lista de estilos de Windows extendidos, vea el *dwExStyle* parámetro para [CreateWindowEx](/windows/win32/api/winuser/nf-winuser-createwindowexw) en el Windows SDK.

*dwStyle*<br/>
Especifica el estilo del control de animación. Aplique cualquier combinación de los estilos de control de ventana y animación descritos en [Estilos](/windows/win32/Controls/animation-control-styles) de control de animación en el Windows SDK.

*Rect*<br/>
Una referencia a una estructura [RECT](/windows/win32/api/windef/ns-windef-rect) que describe el tamaño y la posición de la ventana que se va a crear, en coordenadas de cliente de *pParentWnd*.

*pParentWnd*<br/>
Puntero a la ventana que es el elemento primario del control.

*nID*<br/>
Identificador de ventana secundaria del control.

### <a name="return-value"></a>Valor devuelto

Si es correcta, su valor es distinto de cero. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Se `CreateEx` usa en lugar de [Crear](#create) para aplicar estilos de Windows extendidos, especificados por el **prefacio**de estilo extendido de Windows WS_EX_ .

## <a name="canimatectrlisplaying"></a><a name="isplaying"></a>CAnimateCtrl::IsPlaying

Indica si se está reproduciendo un clip entrelazado de audio y vídeo (AVI).

```
BOOL IsPlaying() const;
```

### <a name="return-value"></a>Valor devuelto

TRUESi se está reproduciendo un clip AVI; de lo contrario, FALSE.

### <a name="remarks"></a>Observaciones

Este método envía el [mensaje ACM_ISPLAYING,](/windows/win32/Controls/acm-isplaying) que se describe en el Windows SDK.

## <a name="canimatectrlopen"></a><a name="open"></a>CAnimateCtrl::Abrir

Llame a esta función para abrir un clip AVI y mostrar su primer fotograma.

```
BOOL Open(LPCTSTR lpszFileName);
BOOL Open(UINT nID);
```

### <a name="parameters"></a>Parámetros

*lpszFileName*<br/>
Objeto `CString` o puntero a una cadena terminada en null que contiene el nombre del archivo AVI o el nombre de un recurso AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se abrió anteriormente para el control de animación, si existe.

*nID*<br/>
Identificador de recursos AVI. Si este parámetro es NULL, el sistema cierra el clip AVI que se abrió anteriormente para el control de animación, si existe.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El recurso AVI se carga desde el módulo que creó el control de animación.

`Open`no admite el sonido en un clip AVI; sólo se pueden abrir clips AVI silenciosos.

Si el control `ACS_AUTOPLAY` de animación tiene el estilo, el control de animación comenzará automáticamente a reproducir el clip inmediatamente después de abrirlo. Seguirá reproduciendo el clip en segundo plano mientras el subproceso continúa ejecutándose. Cuando el clip haya terminado de reproducirse, se repetirá automáticamente.

Si el control `ACS_CENTER` de animación tiene el estilo, el clip AVI se centrará en el control y el tamaño del control no cambiará. Si el control de `ACS_CENTER` animación no tiene el estilo, el control cambiará de tamaño cuando el clip AVI se abra al tamaño de las imágenes en el clip AVI. La posición de la esquina superior izquierda del control no cambiará, solo el tamaño del control.

Si el control `ACS_TRANSPARENT` de animación tiene el estilo, el primer fotograma se dibujará con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlplay"></a><a name="play"></a>CAnimateCtrl::Play

Llame a esta función para reproducir un clip AVI en un control de animación.

```
BOOL Play(
    UINT nFrom,
    UINT nTo,
    UINT nRep);
```

### <a name="parameters"></a>Parámetros

*nDe*<br/>
Indice de base cero del fotograma donde comienza la reproducción. El valor debe ser inferior a 65.536. Un valor de 0 significa comenzar con el primer fotograma del clip AVI.

*nTo*<br/>
Indice de base cero del fotograma donde finaliza la reproducción. El valor debe ser inferior a 65.536. Un valor de - 1 significa terminar con el último fotograma del clip AVI.

*nRep*<br/>
Número de veces que se reproduce el clip AVI. Un valor de - 1 significa reproducir el archivo indefinidamente.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

El control de animación reproducirá el clip en segundo plano mientras el subproceso continúa ejecutándose. Si el control `ACS_TRANSPARENT` de animación tiene estilo, el clip AVI se reproducirá con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlseek"></a><a name="seek"></a>CAnimateCtrl::Buscar

Llame a esta función para mostrar estáticamente un solo fotograma de su clip AVI.

```
BOOL Seek(UINT nTo);
```

### <a name="parameters"></a>Parámetros

*nTo*<br/>
El índice de base cero del fotograma que se va a mostrar. El valor debe ser inferior a 65.536. Un valor de 0 significa mostrar el primer fotograma en el clip AVI. Un valor de -1 significa mostrar el último fotograma en el clip AVI.

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="remarks"></a>Observaciones

Si el control `ACS_TRANSPARENT` de animación tiene estilo, el clip AVI se dibujará con un fondo transparente en lugar del color de fondo especificado en el clip de animación.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="canimatectrlstop"></a><a name="stop"></a>CAnimateCtrl::Stop

Llame a esta función para detener la reproducción de un clip AVI en un control de animación.

```
BOOL Stop();
```

### <a name="return-value"></a>Valor devuelto

Es distinto de cero si es correcto. En caso contrario, es cero.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CAnimateCtrl::CAnimateCtrl](#canimatectrl).

## <a name="see-also"></a>Vea también

[CWnd (clase)](../../mfc/reference/cwnd-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CAnimateCtrl::Create](#create)<br/>
[ON_CONTROL](message-map-macros-mfc.md#on_control)
