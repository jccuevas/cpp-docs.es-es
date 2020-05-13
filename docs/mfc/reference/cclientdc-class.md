---
title: CClientDC (clase)
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
ms.openlocfilehash: abe8a3220fd37a0375fcf37504c715edf4c6962e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352306"
---
# <a name="cclientdc-class"></a>CClientDC (clase)

Se encarga de llamar a las funciones de Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc) en tiempo de construcción y [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) en el momento de la destrucción.

## <a name="syntax"></a>Sintaxis

```
class CClientDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CClientDC::CClientDC](#cclientdc)|Construye un `CClientDC` objeto conectado `CWnd`al archivo .|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CClientDC::m_hWnd](#m_hwnd)|El HWND de la `CClientDC` ventana para la cual esto es válido.|

## <a name="remarks"></a>Observaciones

Esto significa que el contexto `CClientDC` de dispositivo asociado a un objeto es el área de cliente de una ventana.

Para obtener `CClientDC`más información sobre , consulte [Contextos](../../mfc/device-contexts.md)de dispositivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CClientDC`

## <a name="requirements"></a>Requisitos

**Encabezado:** afxwin.h

## <a name="cclientdccclientdc"></a><a name="cclientdc"></a>CClientDC::CClientDC

Construye un `CClientDC` objeto que tiene acceso al área de cliente del [CWnd](../../mfc/reference/cwnd-class.md) al que apunta *pWnd*.

```
explicit CClientDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
La ventana a la que accederá el objeto de contexto de dispositivo al área de cliente.

### <a name="remarks"></a>Observaciones

El constructor llama a la función de Windows [GetDC](/windows/win32/api/winuser/nf-winuser-getdc).

Se produce una `CResourceException`excepción (de `GetDC` tipo ) si se produce un error en la llamada de Windows. Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de visualización comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#42](../../mfc/codesnippet/cpp/cclientdc-class_1.cpp)]

## <a name="cclientdcm_hwnd"></a><a name="m_hwnd"></a>CClientDC::m_hWnd

El `HWND` puntero `CWnd` utilizado para `CClientDC` construir el objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Observaciones

*m_hWnd* es una variable protegida.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CClientDC::CClientDC](#cclientdc).

## <a name="see-also"></a>Consulte también

[Ejemplo de MFC MDI](../../overview/visual-cpp-samples.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)
