---
title: Preguntas más frecuentes sobre contención de controles ATL
ms.date: 11/04/2016
helpviewer_keywords:
- hosting controls using ATL
- ActiveX control containers [C++], ATL control hosting
- ATL, hosting ActiveX controls
- ActiveX controls [C++], hosting
- controls [ATL]
ms.assetid: d4bdfbe0-82ca-4f2f-bb95-cb89bdcc9b53
ms.openlocfilehash: ef175ff83fd641852b27fea8408f1bb7de69f839
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630820"
---
# <a name="atl-control-containment-faq"></a>Preguntas más frecuentes sobre contención de controles ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>¿Qué clases ATL facilitan la contención de controles ActiveX?

El código de hospedaje de controles de ATL no requiere que se use ninguna clase ATL; puede crear simplemente una **"AtlAxWin80"** ventana y use la API de hospedaje de controles si es necesario (para obtener más información, consulte **¿qué es la API de hospedaje de controles de ATL**. Sin embargo, las clases siguientes hacen que las características de contención más fácil de usar.

|Clase|Descripción|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Ajusta un **"AtlAxWin80"** ventana, que proporciona métodos para crear la ventana, crear un control o adjuntar un control a la ventana y recuperar los punteros de interfaz en el objeto host.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Ajusta un **"AtlAxWinLic80"** ventana, que proporciona métodos para crear la ventana, crear un control o adjuntar un control con licencia a la ventana y recuperar los punteros de interfaz en el objeto host.|
|[CComCompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Actúa como clase base para clases de controles ActiveX en función de un recurso de cuadro de diálogo. Estos controles pueden contener otros controles ActiveX.|
|[CAxDialogImpl](../atl/reference/caxdialogimpl-class.md)|Actúa como clase base para las clases de cuadro de diálogo en función de un recurso de cuadro de diálogo. Estos controles pueden contener controles ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Proporciona un método, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), que devuelve un puntero de interfaz en un control, el identificador de su ventana host dado. Además, los contenedores de Windows API exponen por `CWindow` suele facilitar la administración de ventanas.|

## <a name="what-is-the-atl-control-hosting-api"></a>¿Qué es la biblioteca ATL API de hospedaje de controles?

Alojamiento de controles ATL de API es el conjunto de funciones que permite que cualquier ventana para que actúe como un contenedor de controles ActiveX. Estas funciones pueden ser estática o dinámicamente vinculaban a su proyecto, ya que se encuentran disponibles como código fuente y exponen por ATL90.dll. Las funciones de hospedaje de controles se muestran en la tabla siguiente.

|Función|Descripción|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crea un objeto host, se conecta a la ventana suministrada y adjunta un control existente.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crea un objeto host, se conecta a la ventana suministrada y carga un control.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crea un objeto host, se conecta a la ventana suministrada y, a continuación, carga un control (también permite para configurar receptores de eventos).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, de forma similar a [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crea un cuadro de diálogo no modal a partir de un recurso de cuadro de diálogo y devuelve el identificador de ventana.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de un recurso de cuadro de diálogo.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Devuelve el **IUnknown** puntero de interfaz del control hospedado en una ventana.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Devuelve el **IUnknown** puntero de interfaz del objeto host conectado a una ventana.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializa el código de hospedaje de controles.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Desinicializa el código de hospedaje de controles.|

El `HWND` parámetros en las tres primeras funciones deben ser una ventana existente de (casi) cualquier tipo. Si se llama a cualquiera de estas tres funciones explícitamente (normalmente, no tendrá que), no pase un identificador a una ventana que ya está actuando como un host (si lo hace, el objeto de host existente no se liberará).

Las primeras siete funciones llaman a [AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) implícitamente.

> [!NOTE]
>  La API de hospedaje de controles constituye la base de compatibilidad de ATL para contención de controles ActiveX. Sin embargo, suele haber poca necesidad de llamar directamente a estas funciones si aprovechar o hacer un uso completo de las clases contenedoras de ATL. Para obtener más información, consulte [que ATL clases facilitan la contención de controles ActiveX](which-atl-classes-facilitate-activex-control-containment-q.md).

## <a name="what-is-atlaxwin100"></a>¿Qué es AtlAxWin100?

`AtlAxWin100` es el nombre de una clase de ventana que ayuda a proporcionar funcionalidad de hospedaje de controles de ATL. Cuando se crea una instancia de esta clase, el procedimiento de ventana usará automáticamente la API de hospedaje de controles para crear un objeto host asociado a la ventana y cargarlo con el control que se especifica como el título de la ventana.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>¿Cuándo es necesario llamar a AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registra el **"AtlAxWin80"** clase de ventana (junto con un par de mensajes de ventana personalizados), por lo que esta función debe llamarse antes de intentar crear una ventana host. Sin embargo, no siempre es necesario llamar a esta función explícitamente, desde el hospedaje de API (y las clases que las utilizan) a menudo se llame a esta función para usted. No hay ningún daño en la llamada a esta función varias veces.

## <a name="what-is-a-host-object"></a>¿Qué es un objeto Host?

Un objeto host es un objeto COM que representa el contenedor del control ActiveX proporcionado por ATL para una ventana concreta. El objeto host subclases de la ventana del contenedor para que pueda reflejar mensajes al control, proporciona las interfaces de contenedor necesarias para ser utilizado por el control y expone el [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) y [ IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfaces para permitirle configurar el entorno del control.

Puede usar el objeto host para establecer las propiedades de ambientales del contenedor.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>¿Puedo hospedar más de un Control en una única ventana?

No es posible hospedar más de un control en una única ventana host ATL. Cada ventana de host está diseñada para contener exactamente un control a la vez (Esto permite que un mecanismo sencillo para administrar las propiedades ambientales de reflexión y por el control de mensajes). Sin embargo, si necesita el usuario vea varios controles en una sola ventana, resulta sencillo para crear varias ventanas de host como elementos secundarios de esa ventana.

## <a name="can-i-reuse-a-host-window"></a>¿Puedo volver a usar una ventana Host?

No se recomienda volver a usar windows de host. Para garantizar la solidez del código, debe unir la duración de la ventana del host a la duración de un solo control.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>¿Cuándo es necesario llamar a AtlAxWinTerm?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) anula el registro de la **"AtlAxWin80"** clase de ventana. Debe llamar a esta función (si ya no tiene que crear ventanas host) después de que se hayan destruido todas las ventanas de host existente. Si no llama a esta función, la clase de ventana se anula automáticamente cuando finaliza el proceso.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hospedar controles ActiveX mediante ATL AXHost

En esta sección se muestra cómo crear AXHost y cómo hospedar un control ActiveX mediante varias funciones ATL. También muestra cómo obtener acceso a los eventos de control y el receptor (mediante [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) desde el control hospedado. El ejemplo hospeda el control de calendario en una ventana principal o en una ventana secundaria.

Tenga en cuenta la definición de la `USE_METHOD` símbolos. Puede cambiar el valor de este símbolo para variar entre 1 y 8. El valor del símbolo determina cómo se creará el control:

- Para los pares de valores de `USE_METHOD`, la llamada para crear una ventana de las subclases de host y lo convierte en un host de control. Los valores impares, el código crea una ventana secundaria que actúa como un host.

- Para los valores de `USE_METHOD` entre 1 y 4, el acceso al control y la recepción de eventos se consigue con la llamada que también crea el host. Los valores entre 5 y 8 el host para las interfaces de consulta y enlazan el receptor.

A continuación, se muestra un resumen:

|USE_METHOD|administrador de flujos de trabajo|Control de acceso y la recepción de eventos|Función explicada|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Ventana secundaria|Un solo paso|CreateControlLicEx|
|2|Ventana principal|Un solo paso|AtlAxCreateControlLicEx|
|3|Ventana secundaria|Un solo paso|CreateControlEx|
|4|Ventana principal|Un solo paso|AtlAxCreateControlEx|
|5|Ventana secundaria|Varios pasos|CreateControlLic|
|6|Ventana principal|Varios pasos|AtlAxCreateControlLic|
|7|Ventana secundaria|Varios pasos|CreateControl|
|8|Ventana principal|Varios pasos|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Vea también

[Preguntas más frecuentes sobre la contención de controles](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[CAxWindow2T (clase)](../atl/reference/caxwindow2t-class.md)<br/>
[IAxWinHostWindowLic (interfaz)](../atl/reference/iaxwinhostwindowlic-interface.md)