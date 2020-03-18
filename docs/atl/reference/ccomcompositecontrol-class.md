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
ms.openlocfilehash: b57eaf105bfca1a49d53b5e5e99969b0fa2fc82f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79423307"
---
# <a name="ccomcompositecontrol-class"></a>Clase CComCompositeControl

Esta clase proporciona los métodos necesarios para implementar un control compuesto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase, derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), así como de cualquier otra interfaz que desee admitir para el control compuesto.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|El constructor.|
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Llame a este método para notificar o desaconsejar todos los controles hospedados por el control compuesto.|
|[CComCompositeControl::CalcExtent](#calcextent)|Llame a este método para calcular el tamaño en unidades de HIMETRIC del recurso de cuadro de diálogo que se usa para hospedar el control compuesto.|
|[CComCompositeControl:: Create](#create)|Se llama a este método para crear la ventana de control para el control compuesto.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Llame a este método para crear la ventana de control e informar a cualquier control hospedado.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Llame a este método para establecer el color de fondo del control compuesto utilizando el color de fondo del contenedor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CComCompositeControl:: m_hbrBackground](#m_hbrbackground)|Pincel del fondo.|
|[CComCompositeControl:: m_hWndFocus](#m_hwndfocus)|Identificador de la ventana que tiene actualmente el foco.|

## <a name="remarks"></a>Observaciones

Las clases derivadas de la clase `CComCompositeControl` heredan la funcionalidad de un control compuesto ActiveX. Los controles ActiveX derivados de `CComCompositeControl` se hospedan en un cuadro de diálogo estándar. Estos tipos de controles se denominan controles compuestos porque pueden hospedar otros controles (controles nativos de Windows y controles ActiveX).

`CComCompositeControl` identifica el recurso de cuadro de diálogo que se va a utilizar para crear el control compuesto buscando un miembro de datos enumerado en la clase secundaria. El elemento IDD de esta clase secundaria se establece en el identificador de recurso del recurso de cuadro de diálogo que se usará como ventana del control. A continuación se incluye un ejemplo del miembro de datos que la clase derivada de `CComCompositeControl` debe contener para identificar el recurso de cuadro de diálogo que se va a utilizar para la ventana del control:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Los controles compuestos siempre son controles con ventanas, aunque pueden contener controles sin ventanas.

Un control implementado por una clase derivada de `CComCompositeControl`tiene un comportamiento de tabulación predeterminado integrado. Cuando el control recibe el foco mediante la pestaña en una aplicación contenedora, al presionar sucesivamente la tecla TAB, el foco se recorre a través de todos los controles contenidos del control compuesto y, a continuación, del control compuesto y en el siguiente elemento del orden de tabulación del contenedor. El orden de tabulación de los controles hospedados viene determinado por el recurso de cuadro de diálogo y determina el orden en el que se producirá la tabulación.

> [!NOTE]
>  Para que los aceleradores funcionen correctamente con una `CComCompositeControl`, es necesario cargar una tabla de aceleradores a medida que se crea el control, pasar de nuevo el identificador y el número de aceleradores a [IOleControlImpl:: GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo)y, por último, destruir la tabla cuando se libera el control.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl. h

##  <a name="advisesinkmap"></a>CComCompositeControl::AdviseSinkMap

Llame a este método para notificar o desaconsejar todos los controles hospedados por el control compuesto.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
True si se van a notificar todos los controles; en caso contrario, false.

### <a name="return-value"></a>Valor devuelto

|||
|-|-|
|S_OK  |Todos los controles de la asignación del receptor de eventos se conectaron o desconectaron correctamente del origen de eventos.|
|E_FAIL  |No todos los controles del mapa del receptor de eventos se pueden conectar o desconectar correctamente del origen de eventos.|
|E_POINTER  |Este error suele indicar un problema con una entrada en la asignación del receptor de eventos del control o un problema con un argumento de plantilla utilizado en una clase base `IDispEventImpl` o `IDispEventSimpleImpl`.|
|CONNECT_E_ADVISELIMIT  |El punto de conexión ha alcanzado su límite de conexión y no puede aceptar más.|
|CONNECT_E_CANNOTCONNECT  |El receptor no admite la interfaz requerida por este punto de conexión.|
|CONNECT_E_NOCONNECTION  |El valor de cookie no representa una conexión válida. Este error suele indicar un problema con una entrada en la asignación del receptor de eventos del control o un problema con un argumento de plantilla utilizado en una clase base `IDispEventImpl` o `IDispEventSimpleImpl`.|

### <a name="remarks"></a>Observaciones

La implementación base de este método busca en las entradas de la asignación del receptor de eventos. A continuación, se aconseja o se desaconsejan los puntos de conexión a los objetos COM descritos por las entradas del receptor del mapa del receptor de eventos. Este método de miembro también se basa en el hecho de que la clase derivada hereda de una instancia de `IDispEventImpl` para cada control del mapa de receptor que se va a notificar o a que no se recomienda.

##  <a name="calcextent"></a>CComCompositeControl::CalcExtent

Llame a este método para calcular el tamaño en unidades de HIMETRIC del recurso de cuadro de diálogo que se usa para hospedar el control compuesto.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Referencia a una estructura de `SIZE` que se va a rellenar con este método.

### <a name="return-value"></a>Valor devuelto

TRUE si el control está hospedado en un cuadro de diálogo; en caso contrario, FALSE.

### <a name="remarks"></a>Observaciones

El tamaño se devuelve en el parámetro *size* .

##  <a name="create"></a>CComCompositeControl:: Create

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
Datos que se van a pasar al control durante la creación del control. Los datos que se pasan como *dwInitParam* se mostrarán como el parámetro lParam del mensaje [WM_INITDIALOG](/windows/win32/dlgbox/wm-initdialog) , que se enviará al control compuesto cuando se cree.

### <a name="return-value"></a>Valor devuelto

Identificador del cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Observaciones

Normalmente, se llama a este método durante la activación en contexto del control.

##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl

El constructor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Observaciones

Inicializa los miembros de datos [CComCompositeControl:: m_hbrBackground](#m_hbrbackground) y [CComCompositeControl:: m_hWndFocus](#m_hwndfocus) en NULL.

##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl

Destructor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Observaciones

Elimina el objeto de fondo, si existe.

##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow

Llame a este método para crear la ventana de control e informar a los controles hospedados.

```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```

### <a name="parameters"></a>Parámetros

*hWndParent*<br/>
Identificador de la ventana primaria del control.

*rcPos*<br/>
Rectángulo de posición del control compuesto en coordenadas de cliente relativas a *hWndParent*.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Observaciones

Este método llama a [CComCompositeControl:: Create](#create) y [CComCompositeControl:: AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>CComCompositeControl:: m_hbrBackground

Pincel del fondo.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>CComCompositeControl:: m_hWndFocus

Identificador de la ventana que tiene actualmente el foco.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient

Llame a este método para establecer el color de fondo del control compuesto utilizando el color de fondo del contenedor.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente o un error HRESULT en caso de error.

## <a name="see-also"></a>Consulte también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general sobre clases](../../atl/atl-class-overview.md)
