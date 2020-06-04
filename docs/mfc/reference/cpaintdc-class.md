---
title: Clase CPaintDC
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
ms.openlocfilehash: 55342b03454a6dba07bc10ea5f0464c34e0e8db3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374775"
---
# <a name="cpaintdc-class"></a>Clase CPaintDC

Una clase de contexto de dispositivo derivada de [CDC](../../mfc/reference/cdc-class.md).

## <a name="syntax"></a>Sintaxis

```
class CPaintDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPaintDC::CPaintDC](#cpaintdc)|Construye un `CPaintDC` conectado al [CWnd](../../mfc/reference/cwnd-class.md)especificado.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CPaintDC::m_ps](#m_ps)|Contiene el [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) utilizado para pintar el área de cliente.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CPaintDC::m_hWnd](#m_hwnd)|El HWND al `CPaintDC` que está asociado este objeto.|

## <a name="remarks"></a>Observaciones

Realiza un [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint) en tiempo de construcción y [CWnd::EndPaint](../../mfc/reference/cwnd-class.md#endpaint) en tiempo de destrucción.

Un `CPaintDC` objeto solo se puede usar al responder `OnPaint` a un mensaje de [WM_PAINT,](/windows/win32/gdi/wm-paint) normalmente en la función miembro del controlador de mensajes.

Para obtener más `CPaintDC`información sobre el uso de , consulte [Contextos](../../mfc/device-contexts.md)de dispositivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CPaintDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cpaintdccpaintdc"></a><a name="cpaintdc"></a>CPaintDC::CPaintDC

Construye un `CPaintDC` objeto, prepara la ventana de aplicación para pintar y almacena la estructura [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct) en la [m_ps](#m_ps) variable miembro.

```
explicit CPaintDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Apunta al `CWnd` objeto al `CPaintDC` que pertenece el objeto.

### <a name="remarks"></a>Observaciones

Se produce una `CResourceException`excepción (de tipo ) si se produce un error en la llamada [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) de Windows. Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de visualización comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#97](../../mfc/codesnippet/cpp/cpaintdc-class_1.cpp)]

## <a name="cpaintdcm_hwnd"></a><a name="m_hwnd"></a>CPaintDC::m_hWnd

El `HWND` objeto `CPaintDC` al que se adjunta este objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Observaciones

*m_hWnd* es una variable protegida de tipo HWND.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#98](../../mfc/codesnippet/cpp/cpaintdc-class_2.cpp)]

## <a name="cpaintdcm_ps"></a><a name="m_ps"></a>CPaintDC::m_ps

`m_ps`es una variable miembro pública de tipo [PAINTSTRUCT](/windows/win32/api/winuser/ns-winuser-paintstruct).

```
PAINTSTRUCT m_ps;
```

### <a name="remarks"></a>Observaciones

Es el `PAINTSTRUCT` que se pasa y rellena por [CWnd::BeginPaint](../../mfc/reference/cwnd-class.md#beginpaint).

Contiene `PAINTSTRUCT` información que la aplicación utiliza para pintar el `CPaintDC` área de cliente de la ventana asociada a un objeto.

Tenga en cuenta que puede acceder `PAINTSTRUCT`al identificador de contexto de dispositivo a través del archivo . Sin embargo, puede tener acceso `m_hDC` al `CPaintDC` identificador más directamente a través de la variable miembro que hereda de CDC.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CPaintDC::m_hWnd](#m_hwnd).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)
