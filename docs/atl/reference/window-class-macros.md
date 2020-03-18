---
title: Macros de clase de ventana
ms.date: 11/04/2016
f1_keywords:
- atlwin/ATL::DECLARE_WND_CLASS
- atlwin/ATL::DECLARE_WND_SUPERCLASS
- atlwin/ATL::DECLARE_WND_CLASS_EX
ms.assetid: ce18681a-2bab-4453-9895-0f3ea47c2b24
ms.openlocfilehash: c4617a04c199741b97316122456e417a94275e89
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422941"
---
# <a name="window-class-macros"></a>Macros de clase de ventana

Estas macros definen utilidades de clase de ventana.

|||
|-|-|
|[DECLARE_WND_CLASS](#declare_wnd_class)|Permite especificar el nombre de una nueva clase de ventana.|
|[DECLARE_WND_CLASS2](#declare_wnd_class2)|(Visual Studio 2017) Permite especificar el nombre de una nueva clase de ventana y la clase envolvente cuyo procedimiento de ventana utilizará la nueva clase.|
|[DECLARE_WND_SUPERCLASS](#declare_wnd_superclass)|Permite especificar el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana.|
|[DECLARE_WND_CLASS_EX](#declare_wnd_class_ex)|Permite especificar los parámetros de una clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlwin. h

##  <a name="declare_wnd_class"></a>DECLARE_WND_CLASS

Permite especificar el nombre de una nueva clase de ventana. Coloque esta macro en una clase de control del control ActiveX ATL.

```
DECLARE_WND_CLASS( WndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
de Nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

### <a name="remarks"></a>Observaciones

Si usa la opción del compilador/permissive-, DECLARE_WND_CLASS producirá un error del compilador; en su lugar, use DECLARE_WND_CLASS2.

DECLARE_WND_CLASS permite especificar el nombre de una nueva clase de ventana cuya información se administrará mediante [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS define la nueva clase de ventana implementando la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

DECLARE_WND_CLASS especifica los estilos siguientes para la nueva ventana:

- CS_HREDRAW

- CS_VREDRAW

- CS_DBLCLKS

DECLARE_WND_CLASS también especifica el color de fondo de la ventana predeterminada. Use la macro [DECLARE_WND_CLASS_EX](#declare_wnd_class_ex) para proporcionar sus propios estilos y color de fondo.

[CWindowImpl](cwindowimpl-class.md) usa la macro DECLARE_WND_CLASS para crear una ventana basada en una nueva clase de ventana. Para invalidar este comportamiento, use la macro [DECLARE_WND_SUPERCLASS](#declare_wnd_superclass) o proporcione su propia implementación de la función [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) .

Para obtener más información sobre el uso de Windows en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class2"></a>DECLARE_WND_CLASS2

(Visual Studio 2017) Similar a DECLARE_WND_CLASS, pero con un parámetro adicional que evita un error de nombre dependiente al compilar con la opción/permissive-.

```
DECLARE_WND_CLASS2( WndClassName, EnclosingClass )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
de Nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

*EnclosingClass*<br/>
de Nombre de la clase de ventana que incluye la nueva clase de ventana. No puede ser NULL.

### <a name="remarks"></a>Observaciones

Si usa la opción/permissive-, DECLARE_WND_CLASS producirá un error de compilación porque contiene un nombre dependiente. DECLARE_WND_CLASS2 requiere el nombre explícito de la clase en la que se usa esta macro y no provoca el error en la marca/permissive-.
De lo contrario, esta macro es idéntica a [DECLARE_WND_CLASS](#declare_wnd_class).

##  <a name="declare_wnd_superclass"></a>DECLARE_WND_SUPERCLASS

Permite especificar los parámetros de una clase. Coloque esta macro en una clase de control del control ActiveX ATL.

```
DECLARE_WND_SUPERCLASS( WndClassName, OrigWndClassName )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
de Nombre de la clase de ventana que va a ser de la superclase *OrigWndClassName*. Si es NULL, ATL generará un nombre de clase de ventana.

*OrigWndClassName*<br/>
de Nombre de una clase de ventana existente.

### <a name="remarks"></a>Observaciones

Esta macro permite especificar el nombre de una clase de ventana que convertirá en superclase una clase de ventana existente. [CWndClassInfo](cwndclassinfo-class.md) administra la información de la superclase.

DECLARE_WND_SUPERCLASS implementa la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

De forma predeterminada, [CWindowImpl](cwindowimpl-class.md) usa la macro [DECLARE_WND_CLASS](#declare_wnd_class) para crear una ventana basada en una nueva clase de ventana. Al especificar la macro DECLARE_WND_SUPERCLASS en una clase derivada de `CWindowImpl`, la clase de ventana se basará en una clase existente, pero utilizará el procedimiento de ventana. Esta técnica se denomina superclase.

Además de usar las macros DECLARE_WND_CLASS y DECLARE_WND_SUPERCLASS, puede invalidar la función [GetWndClassInfo](cwindowimpl-class.md#getwndclassinfo) con su propia implementación.

Para obtener más información sobre el uso de Windows en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

##  <a name="declare_wnd_class_ex"></a>DECLARE_WND_CLASS_EX

Permite especificar el nombre de una clase de ventana existente en la que se basará una nueva clase de ventana. Coloque esta macro en una clase de control del control ActiveX ATL.

```
DECLARE_WND_CLASS_EX( WndClassName, style, bkgnd )
```

### <a name="parameters"></a>Parámetros

*WndClassName*<br/>
de Nombre de la nueva clase de ventana. Si es NULL, ATL generará un nombre de clase de ventana.

*style*<br/>
de Estilo de la ventana.

*pincel*<br/>
de Color de fondo de la ventana.

### <a name="remarks"></a>Observaciones

Esta macro le permite especificar los parámetros de clase de una nueva clase de ventana, cuya información se administrará mediante [CWndClassInfo](cwndclassinfo-class.md). DECLARE_WND_CLASS_EX define la nueva clase de ventana implementando la siguiente función estática:

[!code-cpp[NVC_ATL_Windowing#127](../../atl/codesnippet/cpp/window-class-macros_1.cpp)]

Si desea utilizar los estilos y el color de fondo predeterminados, utilice la macro [DECLARE_WND_CLASS](#declare_wnd_class) . Para obtener más información sobre el uso de Windows en ATL, vea el artículo [clases de ventana ATL](../../atl/atl-window-classes.md).

## <a name="see-also"></a>Consulte también

[Macros](atl-macros.md)
