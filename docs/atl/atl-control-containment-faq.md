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
ms.openlocfilehash: 36ff3381447b46b28908522d65be9f34fe23addf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317399"
---
# <a name="atl-control-containment-faq"></a>Preguntas más frecuentes sobre contención de controles ATL

## <a name="which-atl-classes-facilitate-activex-control-containment"></a>¿Qué clases ATL facilitan la contención de controles ActiveX?

El código de hospedaje de control de ATL no requiere que use ninguna clase ATL; simplemente puede crear una ventana **"AtlAxWin80"** y utilizar la API de hospedaje de controles si es necesario (para obtener más información, consulte ¿Cuál es la API de **control-hospedaje de ATL**. Sin embargo, las clases siguientes facilitan el uso de las entidades de contención.

|Clase|Descripción|
|-----------|-----------------|
|[CAxWindow](../atl/reference/caxwindow-class.md)|Ajusta una ventana **"AtlAxWin80",** proporcionando métodos para crear la ventana, crear un control o adjuntar un control a la ventana y recuperar punteros de interfaz en el objeto host.|
|[CAxWindow2T](../atl/reference/caxwindow2t-class.md)|Ajusta una ventana **"AtlAxWinLic80",** proporcionando métodos para crear la ventana, crear un control o adjuntar un control con licencia a la ventana y recuperar punteros de interfaz en el objeto host.|
|[CComcompositeControl](../atl/reference/ccomcompositecontrol-class.md)|Actúa como una clase base para las clases de control ActiveX basadas en un recurso de cuadro de diálogo. Estos controles pueden contener otros controles ActiveX.|
|[Caxdialogimpl](../atl/reference/caxdialogimpl-class.md)|Actúa como una clase base para las clases de cuadro de diálogo basadas en un recurso de cuadro de diálogo. Estos cuadros de diálogo pueden contener controles ActiveX.|
|[CWindow](../atl/reference/cwindow-class.md)|Proporciona un método, [GetDlgControl](../atl/reference/cwindow-class.md#getdlgcontrol), que devolverá un puntero de interfaz en un control, dado el identificador de su ventana host. Además, los contenedores `CWindow` de api de Windows expuestos por lo general facilitan la administración de ventanas.|

## <a name="what-is-the-atl-control-hosting-api"></a>¿Qué es la API de hospedaje de controles ATL?

La API de hospedaje de controles de ATL es el conjunto de funciones que permite que cualquier ventana actúe como contenedor de control ActiveX. Estas funciones se pueden vincular estática o dinámicamente en el proyecto, ya que están disponibles como código fuente y expuestos por ATL90.dll. Las funciones de control-alojamiento se enumeran en la tabla siguiente.

|Función|Descripción|
|--------------|-----------------|
|[AtlAxAttachControl](reference/composite-control-global-functions.md#atlaxattachcontrol)|Crea un objeto host, lo conecta a la ventana proporcionada y, a continuación, adjunta un control existente.|
|[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)|Crea un objeto host, lo conecta a la ventana proporcionada y, a continuación, carga un control.|
|[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, similar a [AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol).|
|[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)|Crea un objeto host, lo conecta a la ventana proporcionada y, a continuación, carga un control (también permite configurar receptores de eventos).|
|[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrollicex)|Crea un control ActiveX con licencia, lo inicializa y lo hospeda en la ventana especificada, similar a [AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic).|
|[AtlAxCreateDialog](reference/composite-control-global-functions.md#atlaxcreatedialog)|Crea un cuadro de diálogo no liberador a partir de un recurso de cuadro de diálogo y devuelve el identificador de ventana.|
|[AtlAxDialogBox](reference/composite-control-global-functions.md#atlaxdialogbox)|Crea un cuadro de diálogo modal a partir de un recurso de cuadro de diálogo.|
|[AtlAxGetControl](reference/composite-control-global-functions.md#atlaxgetcontrol)|Devuelve el puntero de interfaz **IUnknown** del control hospedado en una ventana.|
|[AtlAxGetHost](reference/composite-control-global-functions.md#atlaxgethost)|Devuelve el puntero de interfaz **IUnknown** del objeto host conectado a una ventana.|
|[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit)|Inicializa el código de hospedaje de control.|
|[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm)|Uninitializes el código de hospedaje de control.|

Los `HWND` parámetros de las tres primeras funciones deben ser una ventana existente de (casi) cualquier tipo. Si llama explícitamente a cualquiera de estas tres funciones (normalmente, no tendrá que hacerlo), no pase un identificador a una ventana que ya actúe como host (si lo hace, el objeto host existente no se liberará).

Las primeras siete funciones llaman implícitamente a [AtlAxWinInit.](reference/composite-control-global-functions.md#atlaxwininit)

> [!NOTE]
> La API de hospedaje de controles constituye la base de la compatibilidad de ATL para la contención de controles ActiveX. Sin embargo, normalmente hay poca necesidad de llamar a estas funciones directamente si aprovecha o hace pleno uso de las clases contenedoras de ATL. Para obtener más información, consulte [Qué clases ATL facilitan](which-atl-classes-facilitate-activex-control-containment-q.md)la contención de controles ActiveX .

## <a name="what-is-atlaxwin100"></a>¿Qué es AtlAxWin100?

`AtlAxWin100`es el nombre de una clase de ventana que ayuda a proporcionar la funcionalidad de hospedaje de controles de ATL. Al crear una instancia de esta clase, el procedimiento de ventana usará automáticamente la API de hospedaje de controles para crear un objeto host asociado a la ventana y cargarlo con el control que especifique como título de la ventana.

## <a name="when-do-i-need-to-call-atlaxwininit"></a>¿Cuándo es necesario llamar a AtlAxWinInit?

[AtlAxWinInit](reference/composite-control-global-functions.md#atlaxwininit) registra la clase de ventana **"AtlAxWin80"** (además de un par de mensajes de ventana personalizados) por lo que se debe llamar a esta función antes de intentar crear una ventana host. Sin embargo, no siempre es necesario llamar a esta función explícitamente, ya que las API de hospedaje (y las clases que las usan) a menudo llaman a esta función por usted. No hay ningún daño en llamar a esta función más de una vez.

## <a name="what-is-a-host-object"></a>¿Qué es un objeto host?

Un objeto host es un objeto COM que representa el contenedor de control ActiveX proporcionado por ATL para una ventana determinada. El objeto host subclases la ventana contenedora para que pueda reflejar los mensajes para el control, proporciona las interfaces de contenedor necesarias para que las use el control y expone el [IAxWinHostWindow](../atl/reference/iaxwinhostwindow-interface.md) y [IAxWinAmbientDispatch](../atl/reference/iaxwinambientdispatch-interface.md) interfaces para permitirle configurar el entorno del control.

Puede utilizar el objeto host para establecer las propiedades ambientales del contenedor.

## <a name="can-i-host-more-than-one-control-in-a-single-window"></a>¿Puedo hospedar más de un control en una única ventana?

No es posible hospedar más de un control en una sola ventana host ATL. Cada ventana host está diseñada para contener exactamente un control a la vez (esto permite un mecanismo simple para controlar la reflexión de mensajes y las propiedades ambientales por control). Sin embargo, si necesita que el usuario vea varios controles en una sola ventana, es sencillo crear varias ventanas de host como elementos secundarios de esa ventana.

## <a name="can-i-reuse-a-host-window"></a>¿Puedo volver a usar una ventana host?

No se recomienda reutilizar las ventanas de host. Para garantizar la robustez del código, debe vincular la duración de la ventana de host a la duración de un único control.

## <a name="when-do-i-need-to-call-atlaxwinterm"></a>¿Cuándo es necesario llamar a AtlAxWinTerm?

[AtlAxWinTerm](reference/composite-control-global-functions.md#atlaxwinterm) anula el registro de la clase de ventana **"AtlAxWin80".** Debe llamar a esta función (si ya no necesita crear ventanas de host) después de que se hayan destruido todas las ventanas de host existentes. Si no llama a esta función, la clase window se anulará el registro automáticamente cuando finalice el proceso.

## <a name="hosting-activex-controls-using-atl-axhost"></a>Hospedar controles ActiveX mediante ATL AXHost

En el ejemplo de esta sección se muestra cómo crear AXHost y cómo hospedar un control ActiveX mediante varias funciones ATL. También muestra cómo tener acceso a los eventos de control y receptor (mediante [IDispEventImpl](../atl/reference/idispeventimpl-class.md)) desde el control hospedado. El ejemplo hospeda el Calendar control en una ventana principal o en una ventana secundaria.

Observe la definición del `USE_METHOD` símbolo. Puede cambiar el valor de este símbolo para que varíe entre 1 y 8. El valor del símbolo determina cómo se creará el control:

- Para los valores con `USE_METHOD`numeración par de , la llamada para crear el host subclases una ventana y la convierte en un host de control. Para los valores impares, el código crea una ventana secundaria que actúa como host.

- Para los `USE_METHOD` valores de entre 1 y 4, el acceso al control y el hundimiento de eventos se realiza en la llamada que también crea el host. Los valores entre 5 y 8 consultan el host para las interfaces y enganchan el receptor.

A continuación, se muestra un resumen:

|USE_METHOD|Host|Controle el acceso y el hundimiento de eventos|Función demostrada|
|-----------------|----------|--------------------------------------|---------------------------|
|1|Ventana infantil|Un paso|CreateControlLicEx|
|2|Ventana principal|Un paso|AtlAxCreateControlLicEx|
|3|Ventana infantil|Un paso|CreateControlEx|
|4|Ventana principal|Un paso|AtlAxCreateControlEx|
|5|Ventana infantil|Múltiples pasos|CreateControlLic|
|6|Ventana principal|Múltiples pasos|AtlAxCreateControlLic|
|7|Ventana infantil|Múltiples pasos|CreateControl|
|8|Ventana principal|Múltiples pasos|AtlAxCreateControl|

[!code-cpp[NVC_ATL_AxHost#1](../atl/codesnippet/cpp/hosting-activex-controls-using-atl-axhost_1.cpp)]

## <a name="see-also"></a>Consulte también

[Preguntas más frecuentes sobre contención de controles](../atl/atl-control-containment-faq.md)<br/>
[AtlAxCreateControl](reference/composite-control-global-functions.md#atlaxcreatecontrol)<br/>
[AtlAxCreateControlEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[AtlAxCreateControlLic](reference/composite-control-global-functions.md#atlaxcreatecontrollic)<br/>
[AtlAxCreateControlLicEx](reference/composite-control-global-functions.md#atlaxcreatecontrolex)<br/>
[Clase CAxWindow2T](../atl/reference/caxwindow2t-class.md)<br/>
[Interfaz IAxWinHostWindowLic](../atl/reference/iaxwinhostwindowlic-interface.md)
