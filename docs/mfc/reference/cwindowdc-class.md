---
title: Clase CWindowDC
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
ms.openlocfilehash: 0ef9b4917dc834eb8335690f9b0d171245f5c170
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502153"
---
# <a name="cwindowdc-class"></a>Clase CWindowDC

Se deriva de `CDC`.

## <a name="syntax"></a>Sintaxis

```
class CWindowDC : public CDC
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWindowDC::CWindowDC](#cwindowdc)|Construye un objeto `CWindowDC`.|

### <a name="protected-data-members"></a>Miembros de datos protegidos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CWindowDC::m_hWnd](#m_hwnd)|HWND al que está asociado `CWindowDC` este.|

## <a name="remarks"></a>Comentarios

Llama a la función de Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc)en tiempo de construcción y [ReleaseDC](/windows/win32/api/winuser/nf-winuser-releasedc) en el momento de la destrucción. Esto significa que un `CWindowDC` objeto obtiene acceso a todo el área de la pantalla de una [CWnd](../../mfc/reference/cwnd-class.md) (áreas cliente y no cliente).

Para obtener más información sobre `CWindowDC`el uso de, vea contextos de [dispositivos](../../mfc/device-contexts.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CObject](../../mfc/reference/cobject-class.md)

[CDC](../../mfc/reference/cdc-class.md)

`CWindowDC`

## <a name="requirements"></a>Requisitos

Encabezado: AFXWIN. h

##  <a name="cwindowdc"></a>  CWindowDC::CWindowDC

Construye un `CWindowDC` objeto que tiene acceso a todo el área `CWnd` de la pantalla (cliente y no cliente) del objeto al que apunta *PWND*.

```
explicit CWindowDC(CWnd* pWnd);
```

### <a name="parameters"></a>Parámetros

*pWnd*<br/>
Ventana a la que el área de cliente tendrá acceso el objeto de contexto de dispositivo.

### <a name="remarks"></a>Comentarios

El constructor llama a la función de Windows [GetWindowDC](/windows/win32/api/winuser/nf-winuser-getwindowdc).

Si se produce un error `CResourceException`en la llamada de Windows `GetWindowDC` , se produce una excepción (de tipo). Es posible que un contexto de dispositivo no esté disponible si Windows ya ha asignado todos sus contextos de dispositivo disponibles. La aplicación compite por los cinco contextos de presentación comunes disponibles en un momento dado en Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_MFCDocView#188](../../mfc/codesnippet/cpp/cwindowdc-class_1.cpp)]

##  <a name="m_hwnd"></a>  CWindowDC::m_hWnd

El HWND del `CWnd` puntero se utiliza para construir el `CWindowDC` objeto.

```
HWND m_hWnd;
```

### <a name="remarks"></a>Comentarios

`m_hWnd`es una variable protegida de tipo HWND.

### <a name="example"></a>Ejemplo

  Vea el ejemplo de [CWindowDC:: CWindowDC](#cwindowdc).

## <a name="see-also"></a>Vea también

[CDC (clase)](../../mfc/reference/cdc-class.md)<br/>
[Gráfico de jerarquías](../../mfc/hierarchy-chart.md)<br/>
[CDC (clase)](../../mfc/reference/cdc-class.md)
