---
title: Clase CComCompositeControl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComCompositeControl class
- composite controls, CComCompositeControl class
ms.assetid: 1304b931-27e8-4fbc-be8e-bb226ad887fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2308c2c8da67a7d6fe048f3e498e6d7ba1e3cad6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccomcompositecontrol-class"></a>Clase CComCompositeControl
Esta clase proporciona los métodos necesarios para implementar un control compuesto.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class CComCompositeControl : public CComControl<T,CAxDialogImpl<T>>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de [CComObjectRoot](../../atl/reference/ccomobjectroot-class.md) o [CComObjectRootEx](../../atl/reference/ccomobjectrootex-class.md), como también a partir de otras interfaces que desea admitir para el control compuesto.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl::CComCompositeControl](#ccomcompositecontrol)|El constructor.|  
|[CComCompositeControl:: ~ CComCompositeControl](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl:: AdviseSinkMap](#advisesinkmap)|Llame a este método para notificar o no notificar todos los controles hospedados por el control compuesto.|  
|[CComCompositeControl::CalcExtent](#calcextent)|Llamar a este método para calcular el tamaño en **HIMETRIC** unidades del recurso de cuadro de diálogo utilizado para hospedar el control compuesto.|  
|[CComCompositeControl::Create](#create)|Se llama a este método para crear la ventana de control para el control compuesto.|  
|[CComCompositeControl::CreateControlWindow](#createcontrolwindow)|Llamar a este método para crear la ventana de control y notificar cualquier control hospedado.|  
|[CComCompositeControl::SetBackgroundColorFromAmbient](#setbackgroundcolorfromambient)|Llame a este método para establecer el color de fondo del control compuesto con color de fondo del contenedor.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComCompositeControl::m_hbrBackground](#m_hbrbackground)|El pincel del fondo.|  
|[CComCompositeControl::m_hWndFocus](#m_hwndfocus)|El identificador de la ventana que tiene actualmente el foco.|  
  
## <a name="remarks"></a>Comentarios  
 Las clases derivadas de la clase `CComCompositeControl` heredar la funcionalidad de un control compuesto de ActiveX. Controles ActiveX que derivan de `CComCompositeControl` se hospedan en un cuadro de diálogo estándar. Estos tipos de controles se denominan controles compuestos porque son capaz de hospedar otros controles (controles nativos de Windows y controles ActiveX).  
  
 `CComCompositeControl`identifica el recurso de cuadro de diálogo para usarlos al crear el control compuesto mediante la búsqueda de un miembro de datos enumerados en la clase secundaria. El miembro IDD de esta clase secundaria se establece en el identificador de recurso del recurso de cuadro de diálogo que se usará como la ventana del control. El siguiente es un ejemplo del miembro de datos que derivan de la clase `CComCompositeControl` debe contener para identificar el recurso de cuadro de diálogo que se usará para la ventana del control:  
  
 [!code-cpp[NVC_ATL_COM#13](../../atl/codesnippet/cpp/ccomcompositecontrol-class_1.h)]  
  
> [!NOTE]
>  Controles compuestos siempre son controles de ventana, aunque pueden contener controles sin ventana.  
  
 Un control implementado por un `CComCompositeControl`-clase derivada tiene integrado en el comportamiento predeterminado. Cuando el control recibe el foco se tabulan en una aplicación contenedora, consecutivamente al presionar la tecla TAB hará que el foco se recorra cíclicamente por todos de los controles contenido del control compuesto, a continuación, fuera del control compuesto y en el elemento siguiente en el orden de tabulación del contenedor. El orden de tabulación de los controles hospedados viene determinado por el recurso de cuadro de diálogo y determina el orden en que la tabulación se producirá.  
  
> [!NOTE]
>  En orden de aceleradores para funcionar correctamente con un `CComCompositeControl`, es necesario cargar una tabla de aceleradores, tal y como se crea el control, pase el identificador y el número de aceleradores en [IOleControlImpl::GetControlInfo](../../atl/reference/iolecontrolimpl-class.md#getcontrolinfo), y Por último, destruir la tabla cuando se suelta el control.  
  
## <a name="example"></a>Ejemplo  
 [!code-cpp[NVC_ATL_COM#14](../../atl/codesnippet/cpp/ccomcompositecontrol-class_2.h)]  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `WinBase`  
  
 [CComControlBase](../../atl/reference/ccomcontrolbase-class.md)  
  
 [CComControl](../../atl/reference/ccomcontrol-class.md)  
  
 `CComCompositeControl`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlctl.h  
  
##  <a name="advisesinkmap"></a>CComCompositeControl:: AdviseSinkMap  
 Llame a este método para notificar o no notificar todos los controles hospedados por el control compuesto.  
  
```
HRESULT AdviseSinkMap(bool bAdvise);
```  
  
### <a name="parameters"></a>Parámetros  
 `bAdvise`  
 True si todos los controles que se van a recibir información; lo contrario, false.  
  
### <a name="return-value"></a>Valor devuelto  
 `S_OK`  
 Todos los controles en el caso mapa de receptores se han conectado o se desconectó correctamente de su origen de eventos.  
  
 **E_FAIL**  
 No todos los controles en el caso mapa de receptores se podría conectado o desconectado correctamente desde el origen de eventos.  
  
 `E_POINTER`  
 Este error suele indicar un problema con una entrada en el mapa de receptores de eventos del control o un problema con un argumento de plantilla que se usa en un `IDispEventImpl` o `IDispEventSimpleImpl` clase base.  
  
 **CONNECT_E_ADVISELIMIT**  
 El punto de conexión ya ha alcanzado su límite de conexiones y no puede aceptar más.  
  
 **CONNECT_E_CANNOTCONNECT**  
 El receptor no es compatible con la interfaz requerida por este punto de conexión.  
  
 **CONNECT_E_NOCONNECTION**  
 El valor de cookie no representa una conexión válida. Este error suele indicar un problema con una entrada en el mapa de receptores de eventos del control o un problema con un argumento de plantilla que se usa en un `IDispEventImpl` o `IDispEventSimpleImpl` clase base.  
  
### <a name="remarks"></a>Comentarios  
 La implementación base de este método busca a través de las entradas del mapa de receptores en el evento. A continuación, se le informa de o se desaconseja los puntos de conexión a los objetos COM descritos por las entradas de receptor de la asignación receptor de eventos. Este método de miembro también se basa en el hecho de que la clase derivada hereda de una instancia de `IDispEventImpl` para cada control en el mapa de receptores que va a ser aconsejable o desaconsejarán.  
  
##  <a name="calcextent"></a>CComCompositeControl::CalcExtent  
 Llamar a este método para calcular el tamaño en **HIMETRIC** unidades del recurso de cuadro de diálogo utilizado para hospedar el control compuesto.  
  
```
BOOL CalcExtent(SIZE& size);
```  
  
### <a name="parameters"></a>Parámetros  
 `size`  
 Una referencia a un **tamaño** estructura que se rellenará con este método.  
  
### <a name="return-value"></a>Valor devuelto  
 TRUE si el control está hospedado por un cuadro de diálogo; en caso contrario, FALSE.  
  
### <a name="remarks"></a>Comentarios  
 Se devuelve el tamaño en el `size` parámetro.  
  
##  <a name="create"></a>CComCompositeControl::Create  
 Se llama a este método para crear la ventana de control para el control compuesto.  
  
```
HWND Create(
    HWND hWndParent,
    RECT& /* rcPos */,
    LPARAM dwInitParam = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana primaria del control.  
  
 `rcPos`  
 Reservado.  
  
 `dwInitParam`  
 Datos que se va a pasar al control durante la creación del control. Los datos se pasan como `dwInitParam` se mostrarán como el **LPARAM** parámetro de la [WM_INITDIALOG](http://msdn.microsoft.com/library/windows/desktop/ms645428) mensaje, que se enviará al control compuesto cuando se crea.  
  
### <a name="return-value"></a>Valor devuelto  
 Un identificador para el cuadro de diálogo de control compuesto recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Normalmente se llama a este método durante la activación en contexto del control.  
  
##  <a name="ccomcompositecontrol"></a>CComCompositeControl::CComCompositeControl  
 El constructor.  
  
```
CComCompositeControl();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el [CComCompositeControl::m_hbrBackground](#m_hbrbackground) y [CComCompositeControl::m_hWndFocus](#m_hwndfocus) los miembros de datos es NULL.  
  
##  <a name="dtor"></a>CComCompositeControl:: ~ CComCompositeControl  
 Destructor.  
  
```
~CComCompositeControl();
```  
  
### <a name="remarks"></a>Comentarios  
 Elimina el objeto del fondo, si existe.  
  
##  <a name="createcontrolwindow"></a>CComCompositeControl::CreateControlWindow  
 Llamar a este método para crear la ventana de control y notificar los controles hospedados.  
  
```
virtual HWND CreateControlWindow(
    HWND hWndParent,
    RECT& rcPos);
```  
  
### <a name="parameters"></a>Parámetros  
 `hWndParent`  
 Identificador de la ventana primaria del control.  
  
 `rcPos`  
 El rectángulo de posición del control compuesto en cliente coordina relativo a `hWndParent`.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un identificador para el cuadro de diálogo de control compuesto recién creado.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CComCompositeControl::Create](#create) y [CComCompositeControl:: AdviseSinkMap](#advisesinkmap).  
  
##  <a name="m_hbrbackground"></a>CComCompositeControl::m_hbrBackground  
 El pincel del fondo.  
  
```
HBRUSH m_hbrBackground;
```  
  
##  <a name="m_hwndfocus"></a>CComCompositeControl::m_hWndFocus  
 El identificador de la ventana que tiene actualmente el foco.  
  
```
HWND m_hWndFocus;
```  
  
##  <a name="setbackgroundcolorfromambient"></a>CComCompositeControl::SetBackgroundColorFromAmbient  
 Llame a este método para establecer el color de fondo del control compuesto con color de fondo del contenedor.  
  
```
HRESULT SetBackgroundColorFromAmbient();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [Clase CComControl](../../atl/reference/ccomcontrol-class.md)   
 [Fundamentos de controles compuestos](../../atl/atl-composite-control-fundamentals.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
