---
title: CPaintDC (clase)
ms.date: 11/04/2016
f1_keywords:
- CPaintDC
- AFXWIN/CPaintDC
- AFXWIN/CPaintDC::CPaintDC
- AFXWIN/CPaintDC::m_ps
- AFXWIN/CPaintDC::m_hWnd
helpviewer_keywords:
- CPaintDC [MFC], CPaintDC
- CPaintDC [MFC], m_ps
- CPaintDC [MFC], m_hWnd
ms.assetid: 7e245baa-bf9b-403e-a637-7218adf28fab
ms.openlocfilehash: d587f1cfa6ec38dd564da196da8130bffac11302
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503136"
---
# <a name="cpaintdc-class"></a>CPaintDC (clase)

Una clase de contexto de dispositivo derivada de [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Sintaxis

```
class CPaintDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Construye un `CPaintDC` conectado al [CWnd](../../mfc/reference/cwnd-class.md)especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contiene el [paintstruct (](/windows/win32/api/winuser/ns-winuser-paintstruct) que se usa para pintar el área cliente.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|HWND al que está asociado `CPaintDC` este objeto.|

## <a name="remarks"></a>Comentarios

Realiza una [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) en el momento de la construcción y [CWnd:: EndPaint](../../mfc/reference/cwnd-class.md#endpaint) en el momento de la destrucción.

Un `CPaintDC` objeto solo se puede usar cuando se responde a un mensaje [WM_PAINT](/windows/win32/gdi/wm-paint) , normalmente en `OnPaint` la función miembro del controlador de mensajes.

Para obtener más información sobre `CPaintDC`el uso de, vea contextos de [dispositivos](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cpaintdc"></a>  CPaintDC::CPaintDC

Construye un `CPaintDC` objeto, prepara la ventana de la aplicación para pintar y almacena la estructura [paintstruct (](/windows/win32/api/winuser/ns-winuser-paintstruct) en la variable miembro [m_ps](#m_ps) .

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta al `CWnd` objeto al que pertenece el `CPaintDC` objeto.

### <a name="remarks"></a>Comentarios

Se produce una excepción ( `CResourceException`de tipo) si se produce un error en la llamada [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) de Windows. Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de presentación comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CPaintDC::m_hWnd

Al que está asociado `CPaintDC` este objeto. `HWND`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Comentarios

*m_hWnd* es una variable protegida de tipo HWND.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

##  <a name="m_ps"></a>  CPaintDC::m_ps

`m_ps`es una variable de miembro público de tipo [paintstruct (](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Comentarios

Es el `PAINTSTRUCT` que se pasa a y se rellena mediante [CWnd:: BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Contiene información que la aplicación utiliza para pintar el área cliente de la ventana asociada a un `CPaintDC` objeto. `PAINTSTRUCT`

Tenga en cuenta que puede tener acceso al identificador de contexto del `PAINTSTRUCT`dispositivo a través de. Sin embargo, puede tener acceso al identificador más directamente a `m_hDC` través de la `CPaintDC` variable miembro que hereda de CDC.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPaintDC:: m_hWnd](#m_hwnd).

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
