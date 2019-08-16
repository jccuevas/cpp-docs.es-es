---
title: Clase CClientDC (
ms.date: 11/04/2016
f1_keywords:
- CClientDC
- AFXWIN/CClientDC
- AFXWIN/CClientDC::CClientDC
- AFXWIN/CClientDC::m_hWnd
helpviewer_keywords:
- CClientDC [MFC], CClientDC
- CClientDC [MFC], m_hWnd
ms.assetid: 8a871d6b-06f8-496e-9fa3-9a5780848369
ms.openlocfilehash: 46428740d052c70218d4443395777428cdf3c3b0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507335"
---
# <a name="cclientdc-class"></a>Clase CClientDC (

Se encarga de llamar a las funciones de Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) en tiempo de construcción y [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) en el momento de la destrucción.

## <a name="syntax"></a>Sintaxis

```
class CClientDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Construye un `CClientDC` objeto conectado `CWnd`a.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|HWND de la ventana para la que `CClientDC` es válido.|

## <a name="remarks"></a>Comentarios

Esto significa que el contexto de dispositivo asociado a `CClientDC` un objeto es el área de cliente de una ventana.

Para obtener más información `CClientDC`sobre, vea contextos de [dispositivos](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

##  <a name="cclientdc"></a>  CClientDC::CClientDC

Construye un `CClientDC` objeto que tiene acceso al área cliente de [CWnd](../../mfc/reference/cwnd-class.md) a la que apunta *PWND*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Ventana a la que el objeto de contexto de dispositivo tendrá acceso el área de cliente.

### <a name="remarks"></a>Comentarios

El constructor llama a la función de Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Si se produce un error `CResourceException`en la llamada de Windows `GetDC` , se produce una excepción (de tipo). Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de presentación comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CClientDC::m_hWnd

Del puntero utilizado para construir el `CClientDC` objeto. `CWnd` `HWND`

```
HWND m_hWnd;
```

### <a name="remarks"></a>Comentarios

*m_hWnd* es una variable protegida.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CClientDC (:: CClientDC (](#cclientdc).

## <a name="see-also"></a>Vea también

[Ejemplo de MDI de MFC](../../overview/visual-cpp-samples.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)
