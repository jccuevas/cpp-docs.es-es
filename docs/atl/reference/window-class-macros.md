---
title: Macros de clase de ventana
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: 75a6a769770c9de8b26c08fae852197cdb99248e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50503160"
---
# <a name="window-class-macros"></a>Macros de clase de ventana

Estas macros definen las utilidades de clase de ventana.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Permite especificar el nombre de una nueva clase de ventana.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Permite especificar el nombre de una nueva clase de ventana y la ventana cuyo procedimiento usará la nueva clase de la clase envolvente.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Permite especificar el nombre de una clase de ventana existente en el que se basará la nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Le permite especificar los parámetros de una clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin.h

##  <a name="declare_wnd_class"></a>  DECLARE_WND_CLASS

Permite especificar el nombre de una nueva clase de ventana. Colocar esta macro en la clase de control de un control ActiveX de ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[in] El nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

### <a name="remarks"></a>Comentarios

Si usa la opción /permissive-compiler, DECLARE_WND_CLASS provocará un error del compilador; Use DECLARE_WND_CLASS2 en su lugar.

DECLARE_WND_CLASS le permite especificar el nombre de una nueva clase de ventana cuya información se administrarán mediante [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS define la nueva clase de ventana mediante la implementación de la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS especifica los estilos de la nueva ventana siguientes:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS también especifica el color de fondo de la ventana de forma predeterminada. Use la [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) macro para proporcionar sus propios estilos y el color de fondo.

[CWindowImpl](cwindowimpl-class.md) usa la macro DECLARE_WND_CLASS para crear una ventana basada en una nueva clase de ventana. Para invalidar este comportamiento, use el [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) macro, o proporcionar su propia implementación de la [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>  DECLARE_WND_CLASS2

(Visual Studio 2017) Similar a DECLARE_WND_CLASS, pero con un parámetro adicional que evita un error de nombre dependiente al compilar con la /permissive-option.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[in] El nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

*EnclosingClass*<br/>
[in] El nombre de la clase de ventana que contiene la nueva clase de ventana. No puede ser nulo.

### <a name="remarks"></a>Comentarios

Si usas el /permissive-option, DECLARE_WND_CLASS provocará un error de compilación porque contiene un nombre dependiente. DECLARE_WND_CLASS2 requiere que se asigne explícitamente a la clase que esta macro se usa en y no provoca el error en la /permissive-flag.
En caso contrario, es idéntica a esta macro [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>  DECLARE_WND_SUPERCLASS

Le permite especificar los parámetros de una clase. Colocar esta macro en la clase de control de un control ActiveX de ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[in] El nombre de la ventana de la clase que superclase will *OrigWndClassName*. Si es NULL, ATL generará un nombre de clase de ventana.

*OrigWndClassName*<br/>
[in] El nombre de una clase de ventana existente.

### <a name="remarks"></a>Comentarios

Esta macro permite especificar el nombre de una clase de ventana que le superclase de una clase de ventana existente. [CWndClassInfo](cwndclassinfo-class.md) administra la información de la superclase.

DECLARE_WND_SUPERCLASS implementa la función estática siguiente:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

De forma predeterminada, [CWindowImpl](cwindowimpl-class.md) usa el [DECLARE_WND_CLASS](#declare_wnd_class) macro para crear una ventana basada en una clase de ventana nueva. Mediante la especificación de la macro DECLARE_WND_SUPERCLASS en un `CWindowImpl`-clase derivada, la clase de ventana se basará en una clase existente pero va a utilizar el procedimiento de ventana. Esta técnica se denomina crear superclases.

Además de usar las macros DECLARE_WND_CLASS y DECLARE_WND_SUPERCLASS, puede invalidar el [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) función por su propia implementación.

Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>  DECLARE_WND_CLASS_EX

Permite especificar el nombre de una clase de ventana existente en el que se basará la nueva clase de ventana. Colocar esta macro en la clase de control de un control ActiveX de ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
[in] El nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

*Estilo*<br/>
[in] El estilo de la ventana.

*fondo*<br/>
[in] El color de fondo de la ventana.

### <a name="remarks"></a>Comentarios

Esta macro le permite especificar los parámetros de la clase de una nueva clase de ventana, cuya información se administrarán mediante [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX define la nueva clase de ventana mediante la implementación de la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si desea usar los estilos predeterminados y el color de fondo, utilice el [DECLARE_WND_CLASS](#declare_wnd_class) macro. Para obtener más información sobre el uso de ventanas en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Vea también

[Macros](atl-macros.md)

