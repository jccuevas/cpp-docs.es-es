---
title: 'Controles ActiveX MFC: Serializar'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364552"
---
# <a name="mfc-activex-controls-serializing"></a>Controles ActiveX MFC: Serializar

En este artículo se describe cómo serializar un control ActiveX. La serialización es el proceso de leer o escribir en un medio de almacenamiento persistente, como un archivo de disco. La biblioteca microsoft Foundation Class (MFC) proporciona compatibilidad `CObject`integrada para la serialización en la clase . `COleControl`extiende esta compatibilidad a los controles ActiveX mediante el uso de un mecanismo de intercambio de propiedades.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

La serialización de controles ActiveX se implementa reemplazando [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Esta función, llamada durante la carga y el guardado del objeto de control, almacena todas las propiedades implementadas con una variable miembro o una variable miembro con notificación de cambio.

En los temas siguientes se tratan los principales problemas relacionados con la serialización de un control ActiveX:

- Implementación de `DoPropExchange` la función para serializar el objeto de control

- [Personalización del proceso de serialización](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementación de soporte de versiones](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementación de la función DoPropExchange

Cuando se utiliza el Asistente para controles ActiveX para generar el proyecto de control, se agregan automáticamente varias funciones de controlador predeterminadas a la clase de control, incluida la implementación predeterminada de [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). En el ejemplo siguiente se muestra el código agregado a las clases creadas con el Asistente para controles ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Si desea que una propiedad `DoPropExchange` sea persistente, modifique agregando una llamada a la función de intercambio de propiedades. En el ejemplo siguiente se muestra la serialización de una propiedad Boolean CircleShape personalizada, donde la propiedad CircleShape tiene un valor predeterminado **TRUE:**

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

En la tabla siguiente se enumeran las posibles funciones de intercambio de propiedades que puede utilizar para serializar las propiedades del control:

|Funciones de intercambio de propiedades|Propósito|
|---------------------------------|-------------|
|**PX_Blob( )**|Serializa una propiedad de datos de objeto binario grande (BLOB) de tipo.|
|**PX_Bool( )**|Serializa una propiedad booleana de tipo.|
|**PX_Color( )**|Serializa una propiedad de color de tipo.|
|**PX_Currency( )**|Serializa una propiedad de tipo **CY** (moneda).|
|**PX_Double( )**|Serializa una propiedad **double** de tipo.|
|**PX_Font( )**|Serializa una propiedad de tipo Font.|
|**PX_Float( )**|Serializa una propiedad **float** de tipo.|
|**PX_IUnknown( )**|Serializa una propiedad `LPUNKNOWN`de tipo .|
|**PX_Long( )**|Serializa una propiedad de tipo **long.**|
|**PX_Picture( )**|Serializa un tipo Picture propiedad.|
|**PX_Short( )**|Serializa una propiedad **corta** de tipo.|
|**PXstring( )**|Serializa una `CString` propiedad de tipo.|
|**PX_ULong( )**|Serializa un tipo **ULONG** propiedad.|
|**PX_UShort( )**|Serializa una propiedad **USHORT** de tipo.|

Para obtener más información sobre estas funciones de intercambio de propiedades, vea [Persistencia de controles OLE](../mfc/reference/persistence-of-ole-controls.md) en la *referencia de MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Personalización del comportamiento predeterminado de DoPropExchange

La implementación `DoPropertyExchange` predeterminada de (como se muestra en `COleControl`el tema anterior) realiza una llamada a la clase base . Esto serializa el conjunto de `COleControl`propiedades admitido automáticamente por , que utiliza más espacio de almacenamiento que serializar solo las propiedades personalizadas del control. La eliminación de esta llamada permite que el objeto serialice solo las propiedades que considere importantes. Cualquier propiedad stock indica que el control ha implementado no se serializará al guardar o cargar el objeto de control a menos que agregue explícitamente **PX_** llamadas para ellos.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementación de soporte de versiones

La compatibilidad con versiones permite que un control ActiveX revisado agregue nuevas propiedades persistentes y aún así poder detectar y cargar el estado persistente creado por una versión anterior del control. Para que la versión de un control esté disponible como parte de sus datos `DoPropExchange` persistentes, llame a [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) en la función del control. Esta llamada se inserta automáticamente si el control ActiveX se creó mediante el Asistente para controles ActiveX. Se puede quitar si no se necesita compatibilidad con versiones. Sin embargo, el costo en el tamaño del control es muy pequeño (4 bytes) para la flexibilidad adicional que proporciona la compatibilidad con la versión.

Si el control no se creó con el `COleControl::ExchangeVersion` Asistente para controles ActiveX, agregue `DoPropExchange` una llamada insertando la siguiente línea al principio de la función (antes de la llamada a `COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Puede utilizar cualquier **DWORD** como número de versión. Los proyectos generados por el `_wVerMinor` `_wVerMajor` Asistente para controles ActiveX se usan y, como valor predeterminado. Se trata de constantes globales definidas en el archivo de implementación de la clase de control ActiveX del proyecto. En el resto `DoPropExchange` de la función, puede llamar a [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) en cualquier momento para recuperar la versión que está guardando o recuperando.

En el ejemplo siguiente, la versión 1 de este control de ejemplo solo tiene una propiedad "ReleaseDate". La versión 2 agrega una propiedad "OriginalDate". Si se indica al control que cargue el estado persistente desde la versión anterior, inicializa la variable miembro para la nueva propiedad en un valor predeterminado.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

De forma predeterminada, un control "convierte" los datos antiguos al formato más reciente. Por ejemplo, si la versión 2 de un control carga los datos guardados por la versión 1, escribirá el formato de la versión 2 cuando se guarde de nuevo. Si desea que el control guarde los datos **FALSE** en el formato `ExchangeVersion`de última lectura, pase FALSE como tercer parámetro al llamar a . Este tercer parámetro es opcional y es **TRUE** de forma predeterminada.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
