---
title: Macros de clase de ventana
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 18c0912c506bc52421b18d36346204b557c0fc5c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325727"
---
# <a name="window-class-macros"></a>Macros de clase de ventana

Estas macros definen utilidades de clase de ventana.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Le permite especificar el nombre de una nueva clase de ventana.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Le permite especificar el nombre de una nueva clase de ventana y la clase envolvente cuyo procedimiento de ventana utilizará la nueva clase.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Le permite especificar el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Le permite especificar los parámetros de una clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

## <a name="declare_wnd_class"></a><a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Le permite especificar el nombre de una nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[en] El nombre de la nueva clase de ventana. Si NULL, ATL generará un nombre de clase de ventana.

### <a name="remarks"></a>Observaciones

Si está utilizando la opción del compilador /permissive-, DECLARE_WND_CLASS provocará un error del compilador; usar DECLARE_WND_CLASS2 en su lugar.

DECLARE_WND_CLASS permite especificar el nombre de una nueva clase de ventana cuya información será administrada por [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS define la nueva clase de ventana mediante la implementación de la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS especifica los siguientes estilos para la nueva ventana:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS también especifica el color de fondo de la ventana predeterminada. Utilice la macro [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) para proporcionar sus propios estilos y color de fondo.

[CWindowImpl](cwindowimpl-class.md) utiliza la macro de DECLARE_WND_CLASS para crear una ventana basada en una nueva clase de ventana. Para invalidar este comportamiento, use la [macro DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) o proporcione su propia implementación de la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo Clases de [ventana ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class2"></a><a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Similar a DECLARE_WND_CLASS, pero con un parámetro adicional que evita un error de nombre dependiente al compilar con la opción /permissive-.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[en] El nombre de la nueva clase de ventana. Si NULL, ATL generará un nombre de clase de ventana.

*EnclosingClass*<br/>
[en] El nombre de la clase de ventana que encierra la nueva clase de ventana. No puede ser NULL.

### <a name="remarks"></a>Observaciones

Si utiliza la opción /permissive-, DECLARE_WND_CLASS provocará un error de compilación porque contiene un nombre dependiente. DECLARE_WND_CLASS2 requiere que asigne un nombre explícito a la clase en la que se utiliza esta macro y no se produce el error en el indicador /permissive-.
De lo contrario, esta macro es idéntica a [DECLARE_WND_CLASS](#declare_wnd_class).

## <a name="declare_wnd_superclass"></a><a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Le permite especificar los parámetros de una clase. Coloque esta macro en la clase de control de un control ActiveX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[en] El nombre de la clase window que superclase *OrigWndClassName*. Si NULL, ATL generará un nombre de clase de ventana.

*OrigWndClassName*<br/>
[en] El nombre de una clase de ventana existente.

### <a name="remarks"></a>Observaciones

Esta macro le permite especificar el nombre de una clase de ventana que superclase una clase de ventana existente. [CWndClassInfo](cwndclassinfo-class.md) administra la información de la superclase.

DECLARE_WND_SUPERCLASS implementa la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

De forma predeterminada, [CWindowImpl](cwindowimpl-class.md) utiliza la [macro de DECLARE_WND_CLASS](#declare_wnd_class) para crear una ventana basada en una nueva clase de ventana. Al especificar la macro `CWindowImpl`DECLARE_WND_SUPERCLASS en una clase derivada, la clase de ventana se basará en una clase existente, pero usará el procedimiento de ventana. Esta técnica se denomina superclase.

Además de usar las macros DECLARE_WND_CLASS y DECLARE_WND_SUPERCLASS, puede invalidar la función [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) con su propia implementación.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo Clases de [ventana ATL](../../atl/atl-window-classes.md).

## <a name="declare_wnd_class_ex"></a><a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Le permite especificar el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana. Coloque esta macro en la clase de control de un control ActiveX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[en] El nombre de la nueva clase de ventana. Si NULL, ATL generará un nombre de clase de ventana.

*Estilo*<br/>
[en] El estilo de la ventana.

*bkgnd*<br/>
[en] El color de fondo de la ventana.

### <a name="remarks"></a>Observaciones

Esta macro permite especificar los parámetros de clase de una nueva clase de ventana, cuya información será administrada por [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX define la nueva clase de ventana mediante la implementación de la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si desea utilizar los estilos predeterminados y el color de fondo, utilice la macro [DECLARE_WND_CLASS.](#declare_wnd_class) Para obtener más información sobre el uso de ventanas en ATL, vea el artículo Clases de [ventana ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Consulte también

[Macros](atl-macros.md)
