---
title: Clase CComCompositeControl
ms.date: 11/04/2016
f1_keywords:
- CComCompositeControl
- ATLCTL/ATL::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::CComCompositeControl
- ATLCTL/ATL::CComCompositeControl::AdviseSinkMap
- ATLCTL/ATL::CComCompositeControl::CalcExtent
- ATLCTL/ATL::CComCompositeControl::Create
- ATLCTL/ATL::CComCompositeControl::CreateControlWindow
- ATLCTL/ATL::CComCompositeControl::SetBackgroundColorFromAmbient
- ATLCTL/ATL::CComCompositeControl::m_hbrBackground
- ATLCTL/ATL::CComCompositeControl::m_hWndFocus
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
ms.openlocfilehash: 700a8047ab1fa9df85c8e6530eb3eed5f29bd3d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320803"
---
# <a name="ccomcompositecontrol-class"></a>Clase CComCompositeControl

Esta clase proporciona los métodos necesarios para implementar un control compuesto.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir para el control compuesto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|El constructor.|
|[CComCompositeControl::-CComCompositeControl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Llame a este método para aconsejar o desaconsejar todos los controles hospedados por el control compuesto.|
|[CComCompositeControl::CalcExtent](#calcextent)|Llame a este método para calcular el tamaño en unidades HIMETRIC del recurso de cuadro de diálogo utilizado para hospedar el control compuesto.|
|[CComCompositeControl::Crear](#create)|Se llama a este método para crear la ventana de control para el control compuesto.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Llame a este método para crear la ventana de control y aconsejar cualquier control hospedado.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Llame a este método para establecer el color de fondo del control compuesto mediante el color de fondo del contenedor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|Pincel del fondo.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|El identificador de la ventana que actualmente tiene el foco.|

## <a name="remarks"></a>Observaciones

Las clases `CComCompositeControl` derivadas de la clase heredan la funcionalidad de un control compuesto ActiveX. Los controles ActiveX `CComCompositeControl` derivados de se hospedan en un cuadro de diálogo estándar. Estos tipos de controles se denominan controles compuestos porque pueden hospedar otros controles (controles nativos de Windows y controles ActiveX).

`CComCompositeControl`identifica el recurso de cuadro de diálogo que se usará en la creación del control compuesto buscando un miembro de datos enumerado en la clase secundaria. El IDD de miembro de esta clase secundaria se establece en el identificador de recurso del recurso de cuadro de diálogo que se usará como ventana del control. A continuación se muestra un ejemplo del miembro `CComCompositeControl` de datos del que debe contener la clase derivada para identificar el recurso de cuadro de diálogo que se usará para la ventana del control:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
> Los controles compuestos siempre son controles con ventanas, aunque pueden contener controles sin ventanas.

Un control implementado `CComCompositeControl`por una clase derivada tiene el comportamiento de tabulación predeterminado integrado. Cuando el control recibe el foco al tener pestañas en una aplicación contenedora, presionar sucesivamente la tecla TAB hará que el foco se recicle a través de todos los controles contenidos del control compuesto, a continuación, fuera del control compuesto y en el siguiente elemento en el orden de tabulación del contenedor. El orden de tabulación de los controles hospedados viene determinado por el recurso de cuadro de diálogo y determina el orden en el que se producirá la tabulación.

> [!NOTE]
> Para que los aceleradores funcionen correctamente con un `CComCompositeControl`, es necesario cargar una tabla de aceleradores a medida que se crea el control, pasar el identificador y el número de aceleradores de nuevo en [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)y, finalmente, destruir la tabla cuando se libera el control.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

## <a name="ccomcompositecontroladvisesinkmap"></a><a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Llame a este método para aconsejar o desaconsejar todos los controles hospedados por el control compuesto.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
True si se deben tener en cuenta todos los controles; de lo contrario falso.

### <a name="return-value"></a>Valor devuelto

|||
|-|-|
|S_OK  |Todos los controles del mapa del receptor de eventos se conectaron o desconectaron correctamente de su origen de eventos.|
|E_FAIL  |No todos los controles del mapa del receptor de eventos se pueden conectar o desconectar correctamente de su origen de eventos.|
|E_POINTER  |Este error suele indicar un problema con una entrada en el mapa del receptor `IDispEventImpl` de `IDispEventSimpleImpl` eventos del control o un problema con un argumento de plantilla utilizado en una clase base o.|
|CONNECT_E_ADVISELIMIT  |El punto de conexión ha alcanzado su límite de conexión y no puede aceptar más.|
|CONNECT_E_CANNOTCONNECT  |El receptor no admite la interfaz requerida por este punto de conexión.|
|CONNECT_E_NOCONNECTION  |El valor de cookie no representa una conexión válida. Este error suele indicar un problema con una entrada en el mapa del receptor `IDispEventImpl` de `IDispEventSimpleImpl` eventos del control o un problema con un argumento de plantilla utilizado en una clase base o.|

### <a name="remarks"></a>Observaciones

La implementación base de este método busca a través de las entradas en el mapa del receptor de eventos. A continuación, aconseja o desaconseja los puntos de conexión a los objetos COM descritos por las entradas de receptor del mapa de receptores de eventos. Este método miembro también se basa en el hecho de `IDispEventImpl` que la clase derivada hereda de una instancia de cada control en el mapa de receptores que se debe tener en cuenta o no se debe aconsejar.

## <a name="ccomcompositecontrolcalcextent"></a><a name="calcextent"></a>CComCompositeControl::CalcExtent

Llame a este método para calcular el tamaño en unidades HIMETRIC del recurso de cuadro de diálogo utilizado para hospedar el control compuesto.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
Una referencia `SIZE` a una estructura que se debe rellenar con este método.

### <a name="return-value"></a>Valor devuelto

TRUESi el control está hospedado por un cuadro de diálogo; de lo contrario FALSO.

### <a name="remarks"></a>Observaciones

El tamaño se devuelve en el parámetro *size.*

## <a name="ccomcompositecontrolcreate"></a><a name="create"></a>CComCompositeControl::Crear

Se llama a este método para crear la ventana de control para el control compuesto.

```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la ventana primaria del control.

*rcPos*<br/>
Reservado.

*dwInitParam*<br/>
Datos que se pasarán al control durante la creación del control. Los datos pasados como *dwInitParam* se mostrarán como el parámetro LPARAM del [mensaje WM_INITDIALOG,](/windows/win32/dlgbox/wm-initdialog) que se enviará al control compuesto cuando se cree.

### <a name="return-value"></a>Valor devuelto

Identificador del cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Observaciones

Normalmente se llama a este método durante la activación in situ del control.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

El constructor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos [CComCompositeControl::m_hbrBackground](#m_hbrbackground) y [CComCompositeControl::m_hWndFocus](#m_hwndfocus) en NULL.

## <a name="ccomcompositecontrolccomcompositecontrol"></a><a name="dtor"></a>CComCompositeControl::-CComCompositeControl

Destructor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Observaciones

Elimina el objeto de fondo, si existe.

## <a name="ccomcompositecontrolcreatecontrolwindow"></a><a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Llame a este método para crear la ventana de control y aconsejar a los controles hospedados.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la ventana primaria del control.

*rcPos*<br/>
El rectángulo de posición del control compuesto en coordenadas de cliente en relación con *hWndParent*.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador al cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Observaciones

Este método llama a [CComCompositeControl::Create](#create) y [CComCompositeControl::AdviseSinkMap](#advisesinkmap).

## <a name="ccomcompositecontrolm_hbrbackground"></a><a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground

Pincel del fondo.

```
HBRUSH m_hbrBackground;
```

## <a name="ccomcompositecontrolm_hwndfocus"></a><a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus

El identificador de la ventana que actualmente tiene el foco.

```
HWND m_hWndFocus;
```

## <a name="ccomcompositecontrolsetbackgroundcolorfromambient"></a><a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Llame a este método para establecer el color de fondo del control compuesto mediante el color de fondo del contenedor.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK en caso de éxito o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[Clase CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
