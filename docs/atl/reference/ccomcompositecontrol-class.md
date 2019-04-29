---
title: CComCompositeControl (clase)
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
ms.openlocfilehash: f1a9a2d0628b3683f047ce9858d809040438db03
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260245"
---
# <a name="ccomcompositecontrol-class"></a>CComCompositeControl (clase)

Esta clase proporciona los métodos necesarios para implementar un control compuesto.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <class T>
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir del resto de interfaces que desea admitir para el control compuesto.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|El constructor.|
|[CComCompositeControl::~CComCompositeControl](#dtor)|Destructor.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCompositeControl::AdviseSinkMap](#advisesinkmap)|Llame a este método para notificar o no notificar todos los controles alojados por el control compuesto.|
|[CComCompositeControl::CalcExtent](#calcextent)|Llame a este método para calcular el tamaño en unidades HIMETRIC del recurso de cuadro de diálogo usa para hospedar un control compuesto.|
|[CComCompositeControl::Create](#create)|Se llama a este método para crear la ventana de control para el control compuesto.|
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Llame a este método para crear la ventana de control y aconseja cualquier control hospedado.|
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Llame a este método para establecer el color de fondo del control compuesto con el color de fondo del contenedor.|

### <a name="public-data-members"></a>Miembros de datos públicos

|Name|Descripción|
|----------|-----------------|
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|El pincel del fondo.|
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|El identificador de la ventana que tiene actualmente el foco.|

## <a name="remarks"></a>Comentarios

Las clases derivadas de la clase `CComCompositeControl` hereda la funcionalidad de un control compuesto de ActiveX. Controles ActiveX derivados `CComCompositeControl` se hospedan en un cuadro de diálogo estándar. Estos tipos de controles se denominan controles compuestos porque son capaz de hospedar otros controles (controles de Windows nativos y los controles ActiveX).

`CComCompositeControl` identifica el recurso de cuadro de diálogo debe utilizar para crear un control compuesto mediante la búsqueda de un miembro de datos enumerados en la clase secundaria. El miembro IDD de esta clase secundaria se establece en el identificador de recurso del recurso de cuadro de diálogo que se usará como la ventana del control. El siguiente es un ejemplo del miembro de datos que se deriva de la clase `CComCompositeControl` debe contener para identificar el recurso de cuadro de diálogo que se usará para la ventana del control:

[!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]

> [!NOTE]
>  Los controles compuestos siempre son controles con ventanas, aunque pueden contener controles sin ventana.

Un control que implementa un `CComCompositeControl`-clase derivada tiene integrado el comportamiento predeterminado. Cuando el control recibe el foco se tabulan en una aplicación contenedora, consecutivamente al presionar la tecla TAB hará que el foco se recorra cíclicamente por todos los controles del control compuesto que contiene, a continuación, fuera de un control compuesto y sesión en el siguiente elemento en el orden de tabulación del contenedor. El orden de tabulación de los controles hospedados viene determinada por el recurso de cuadro de diálogo y determina el orden en que la tabulación se producirá.

> [!NOTE]
>  En orden para aceleradores funcione correctamente con un `CComCompositeControl`, es necesario cargar una tabla de aceleradores, ya que se crea el control, pase el identificador y el número de aceleradores en [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), y destruir, por último, en la tabla cuando se suelta el control.

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`WinBase`

[CComControlBase](../../atl/reference/ccomcontrolbase-class.md)

[CComControl](../../atl/reference/ccomcontrol-class.md)

`CComCompositeControl`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlctl.h

##  <a name="advisesinkmap"></a>  CComCompositeControl::AdviseSinkMap

Llame a este método para notificar o no notificar todos los controles alojados por el control compuesto.

```
HRESULT AdviseSinkMap(bool bAdvise);
```

### <a name="parameters"></a>Parámetros

*bAdvise*<br/>
True si todos los controles son recibir información; en caso contrario, false.

### <a name="return-value"></a>Valor devuelto

|||
|-|-|
|S_OK  |Todos los controles en caso de mapa de receptores se han conectado o desconectado correctamente de su origen de eventos.|
|E_FAIL  |No todos los controles en caso de mapa de receptores de podría ser conectado o desconectado correctamente de su origen de eventos.|
|E_POINTER  |Este error suele indicar un problema con una entrada en el mapa de receptores de eventos del control o un problema con un argumento de plantilla utilizado en un `IDispEventImpl` o `IDispEventSimpleImpl` clase base.|
|CONNECT_E_ADVISELIMIT  |El punto de conexión ya ha alcanzado su límite de conexiones y no puede aceptar nada más.|
|CONNECT_E_CANNOTCONNECT  |El receptor no es compatible con la interfaz requerida por este punto de conexión.|
|CONNECT_E_NOCONNECTION  |El valor de cookie no representa una conexión válida. Este error suele indicar un problema con una entrada en el mapa de receptores de eventos del control o un problema con un argumento de plantilla utilizado en un `IDispEventImpl` o `IDispEventSimpleImpl` clase base.|

### <a name="remarks"></a>Comentarios

La implementación base de este método busca a través de las entradas del mapa de receptor de eventos. A continuación, aconseja o no notifica los puntos de conexión a los objetos COM que se describen las entradas del mapa de receptor de eventos receptor. Este método de miembro también se basa en el hecho de que la clase derivada hereda de una instancia de `IDispEventImpl` para todos los controles en el mapa de receptores que se va a aconsejable o no notificar.

##  <a name="calcextent"></a>  CComCompositeControl::CalcExtent

Llame a este método para calcular el tamaño en unidades HIMETRIC del recurso de cuadro de diálogo usa para hospedar un control compuesto.

```
BOOL CalcExtent(SIZE& size);
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Una referencia a un `SIZE` estructura que se rellenará con este método.

### <a name="return-value"></a>Valor devuelto

TRUE si el control está hospedado por un cuadro de diálogo; en caso contrario, FALSE.

### <a name="remarks"></a>Comentarios

Se devuelve el tamaño en el *tamaño* parámetro.

##  <a name="create"></a>  CComCompositeControl::Create

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
Datos que se pasarán al control durante la creación del control. Los datos se pasan como *dwInitParam* aparecerá como el parámetro LPARAM de la [WM_INITDIALOG](/windows/desktop/dlgbox/wm-initdialog) mensaje, que se enviará al control compuesto cuando se crea.

### <a name="return-value"></a>Valor devuelto

Un identificador para el cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Comentarios

Normalmente, este método se llama durante la activación en contexto del control.

##  <a name="ccomcompositecontrol"></a>  CComCompositeControl::CComCompositeControl

El constructor.

```
CComCompositeControl();
```

### <a name="remarks"></a>Comentarios

Inicializa el [CComCompositeControl::m_hbrBackground](#m_hbrbackground) y [CComCompositeControl::m_hWndFocus](#m_hwndfocus) los miembros de datos es NULL.

##  <a name="dtor"></a>  CComCompositeControl::~CComCompositeControl

Destructor.

```
~CComCompositeControl();
```

### <a name="remarks"></a>Comentarios

Elimina el objeto en segundo plano, si existe.

##  <a name="createcontrolwindow"></a>  CComCompositeControl::CreateControlWindow

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
Coordina el rectángulo de posición de un control compuesto en el cliente respecto a *hWndParent*.

### <a name="return-value"></a>Valor devuelto

Devuelve un identificador para el cuadro de diálogo de control compuesto recién creado.

### <a name="remarks"></a>Comentarios

Este método llama a [CComCompositeControl::Create](#create) y [CComCompositeControl:: AdviseSinkMap](#advisesinkmap).

##  <a name="m_hbrbackground"></a>  CComCompositeControl::m_hbrBackground

El pincel del fondo.

```
HBRUSH m_hbrBackground;
```

##  <a name="m_hwndfocus"></a>  CComCompositeControl::m_hWndFocus

El identificador de la ventana que tiene actualmente el foco.

```
HWND m_hWndFocus;
```

##  <a name="setbackgroundcolorfromambient"></a>  CComCompositeControl::SetBackgroundColorFromAmbient

Llame a este método para establecer el color de fondo del control compuesto con el color de fondo del contenedor.

```
HRESULT SetBackgroundColorFromAmbient();
```

### <a name="return-value"></a>Valor devuelto

Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.

## <a name="see-also"></a>Vea también

[CComControl (clase)](../../atl/reference/ccomcontrol-class.md)<br/>
[Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
