---
title: CWindowDC (clase)
ms.date: 11/04/2016
f1_keywords:
- CWindowDC
- AFXWIN/CWindowDC
- AFXWIN/CWindowDC::CWindowDC
- AFXWIN/CWindowDC::m_hWnd
helpviewer_keywords:
- CWindowDC [MFC], CWindowDC
- CWindowDC [MFC], m_hWnd
ms.assetid: 876a3641-4cde-471c-b0d1-fe58b32af79c
ms.openlocfilehash: 89a822280ddebca942016f9a3a334a7128d8456a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371979"
---
# <a name="cwindowdc-class"></a>CWindowDC (clase)

Se deriva de `CDC`.

## <a name="syntax"></a>Sintaxis

```
class CWindowDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Construye un objeto `CWindowDC`.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|Nombre|Descripción|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|El HWND al `CWindowDC` que está conectado.|

## <a name="remarks"></a>Observaciones

Llama a la función de Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)en tiempo de construcción y [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) en tiempo de destrucción. Esto significa `CWindowDC` que un objeto tiene acceso a toda el área de pantalla de un [CWnd](../../mfc/reference/cwnd-class.md) (áreas cliente y no cliente).

Para obtener más `CWindowDC`información sobre el uso de , consulte [Contextos](../../mfc/device-contexts.md)de dispositivo .

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Requisitos

Encabezado: afxwin.h

## <a name="cwindowdccwindowdc"></a><a name="cwindowdc"></a>CWindowDC::CWindowDC

Construye un `CWindowDC` objeto que tiene acceso a todo el área `CWnd` de pantalla (cliente y no cliente) del objeto al que apunta *pWnd*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
La ventana a la que accederá el objeto de contexto de dispositivo al área de cliente.

### <a name="remarks"></a>Observaciones

El constructor llama a la función de Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Se produce una `CResourceException`excepción (de `GetWindowDC` tipo ) si se produce un error en la llamada de Windows. Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de visualización comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

## <a name="cwindowdcm_hwnd"></a><a name="m_hwnd"></a>CWindowDC::m_hWnd

El HWND `CWnd` del puntero se `CWindowDC` utiliza para construir el objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Observaciones

`m_hWnd`es una variable protegida de tipo HWND.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWindowDC::CWindowDC](#cwindowdc).

## <a name="see-also"></a>Consulte también

[Clase CDC](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[Clase CDC](../../mfc/reference/cdc-class.md)
