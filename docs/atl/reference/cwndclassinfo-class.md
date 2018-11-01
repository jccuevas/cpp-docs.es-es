---
title: CWndClassInfo (clase)
ms.date: 11/04/2016
f1_keywords:
- CWndClassInfo
- ATLWIN/ATL::CWndClassInfo
- ATLWIN/ATL::Register
- ATLWIN/ATL::m_atom
- ATLWIN/ATL::m_bSystemCursor
- ATLWIN/ATL::m_lpszCursorID
- ATLWIN/ATL::m_lpszOrigName
- ATLWIN/ATL::m_szAutoName
- ATLWIN/ATL::m_wc
- ATLWIN/ATL::pWndProc
helpviewer_keywords:
- CWndClassInfo class
ms.assetid: c36fe7e1-75f1-4cf5-a06f-9f59c43fe6fb
ms.openlocfilehash: 2ffe37059eb6ab81eb9dd67243ba125766b92dfc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50467306"
---
# <a name="cwndclassinfo-class"></a>CWndClassInfo (clase)

Esta clase proporciona métodos para registrar información de una clase de ventana.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
class CWndClassInfo
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|||
|-|-|
|[Registro](#register)|Registra la clase de ventana.|

### <a name="data-members"></a>Miembros de datos

|||
|-|-|
|[m_atom](#m_atom)|Identifica la clase de ventana registrada.|
|[m_bSystemCursor](#m_bsystemcursor)|Especifica si el recurso de cursor hace referencia a un cursor de sistema o a un cursor dentro de un recurso de módulo.|
|[m_lpszCursorID](#m_lpszcursorid)|Especifica el nombre del recurso de cursor.|
|[m_lpszOrigName](#m_lpszorigname)|Contiene el nombre de una clase de ventana existente.|
|[m_szAutoName](#m_szautoname)|Contiene un nombre generado ATL de la clase de ventana.|
|[m_wc](#m_wc)|Mantiene la información de la clase de ventana en un `WNDCLASSEX` estructura.|
|[pWndProc](#pwndproc)|Señala el procedimiento de ventana de una clase de ventana existente.|

## <a name="remarks"></a>Comentarios

`CWndClassInfo` administra la información de una clase de ventana. Se suele usar `CWndClassInfo` a través de uno de tres macros, DECLARE_WND_CLASS, DECLARE_WND_CLASS_EX o DECLARE_WND_SUPERCLASS, tal como se describe en la tabla siguiente:

|Macro|Descripción|
|-----------|-----------------|
|[DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class)|`CWndClassInfo` registra la información para una nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex)|`CWndClassInfo` registra la información para una nueva clase de ventana, incluidos los parámetros de la clase.|
|[DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass)|`CWndClassInfo` registra la información para una clase de ventana que se basa en una clase existente, pero usa un procedimiento de ventana diferente. Esta técnica se denomina crear superclases.|

De forma predeterminada, [CWindowImpl](../../atl/reference/cwindowimpl-class.md) incluye la `DECLARE_WND_CLASS` macro para crear una ventana basada en una clase de ventana nueva. DECLARE_WND_CLASS proporciona los estilos predeterminados y el color de fondo del control. Si desea especificar el estilo y color de fondo por sí mismo, derive la clase de `CWindowImpl` e incluya la macro DECLARE_WND_CLASS_EX en la definición de clase.

Si desea crear una ventana basada en una clase de ventana existente, derive la clase de `CWindowImpl` e incluya la macro DECLARE_WND_SUPERCLASS en la definición de clase. Por ejemplo:

[!code-cpp[NVC_ATL_Windowing#43](../../atl/codesnippet/cpp/cwndclassinfo-class_1.h)]

Para obtener más información acerca de las clases de ventana, consulte [clases de ventana](/windows/desktop/winmsg/window-classes) en el SDK de Windows.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="m_atom"></a>  CWndClassInfo::m_atom

Contiene el identificador único para la clase de ventana registrada.

```
ATOM m_atom;
```

##  <a name="m_bsystemcursor"></a>  CWndClassInfo::m_bSystemCursor

Si es TRUE, se cargará el recurso de cursor del sistema cuando se registra la clase de ventana.

```
BOOL m_bSystemCursor;
```

### <a name="remarks"></a>Comentarios

En caso contrario, se cargará el recurso de cursor contenido en el módulo.

`CWndClassInfo` usa `m_bSystemCursor` solo cuando el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro se ha especificado. En este caso, `m_bSystemCursor` se inicializa en TRUE. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

##  <a name="m_lpszcursorid"></a>  CWndClassInfo::m_lpszCursorID

Especifica el nombre del recurso de cursor o el identificador de recurso en la palabra de orden inferior y cero en la palabra de orden superior.

```
LPCTSTR m_lpszCursorID;
```

### <a name="remarks"></a>Comentarios

Cuando se registra la clase de ventana, el identificador de cursor identificado por `m_lpszCursorID` se recuperan y almacenan por [m_wc](#m_wc).

`CWndClassInfo` usa `m_lpszCursorID` solo cuando el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro se ha especificado. En este caso, `m_lpszCursorID` se inicializa en IDC_ARROW. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

##  <a name="m_lpszorigname"></a>  CWndClassInfo::m_lpszOrigName

Contiene el nombre de una clase de ventana existente.

```
LPCTSTR m_lpszOrigName;
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo` usa `m_lpszOrigName` sólo al incluir el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro en la definición de clase. En este caso, `CWndClassInfo` registra una clase de ventana en función de la clase con el nombre `m_lpszOrigName`. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

##  <a name="m_szautoname"></a>  CWndClassInfo::m_szAutoName

Contiene el nombre de la clase de ventana.

```
TCHAR m_szAutoName[13];
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo` usa `m_szAutoName` solo si se pasa NULL la `WndClassName` parámetro [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class), el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) o [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) . ATL construirá un nombre cuando se registra la clase de ventana.

##  <a name="m_wc"></a>  CWndClassInfo::m_wc

Mantiene la información de la clase de ventana en un [WNDCLASSEX](https://msdn.microsoft.com/library/windows/desktop/ms633577) estructura.

```
WNDCLASSEX m_wc;
```

### <a name="remarks"></a>Comentarios

Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `m_wc` contiene información sobre una nueva clase de ventana.

Si ha especificado el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `m_wc` contiene información sobre una superclase, una clase de ventana que se basa en una clase existente, pero usa un procedimiento de ventana diferente. [m_lpszOrigName](#m_lpszorigname) y [pWndProc](#pwndproc) guardar nombre de la clase de ventana existente y el procedimiento de ventana, respectivamente.

##  <a name="pwndproc"></a>  CWndClassInfo::pWndProc

Señala el procedimiento de ventana de una clase de ventana existente.

```
WNDPROC pWndProc;
```

### <a name="remarks"></a>Comentarios

`CWndClassInfo` usa `pWndProc` sólo al incluir el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro en la definición de clase. En este caso, `CWndClassInfo` registra una clase de ventana que se basa en una clase existente, pero usa un procedimiento de ventana diferente. Procedimiento de ventana de la clase de ventana existente se guarda en `pWndProc`. Para obtener más información, consulte el [CWndClassInfo](../../atl/reference/cwndclassinfo-class.md) información general.

##  <a name="register"></a>  CWndClassInfo::Register

Lo llama [CWindowImpl:: Create](../../atl/reference/cwindowimpl-class.md#create) para registrar la clase de ventana si aún no se ha registrado.

```
ATOM Register(WNDPROC* pProc);
```

### <a name="parameters"></a>Parámetros

*pProc*<br/>
[out] Especifica el procedimiento de ventana original de una clase de ventana existente.

### <a name="return-value"></a>Valor devuelto

Si es correcto, un átomo que identifica la clase de ventana que se está registrada. En caso contrario, es 0.

### <a name="remarks"></a>Comentarios

Si ha especificado el [DECLARE_WND_CLASS](window-class-macros.md#declare_wnd_class) (el valor predeterminado en [CWindowImpl](../../atl/reference/cwindowimpl-class.md)) o el [DECLARE_WND_CLASS_EX](window-class-macros.md#declare_wnd_class_ex) macro, `Register` registra una nueva clase de ventana. En este caso, el *pProc* no se usa el parámetro.

Si ha especificado el [DECLARE_WND_SUPERCLASS](window-class-macros.md#declare_wnd_superclass) macro, `Register` registra una superclase, una clase de ventana que se basa en una clase existente, pero usa un procedimiento de ventana diferente. Procedimiento de ventana de la clase de ventana existente se devuelve en *pProc*.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)