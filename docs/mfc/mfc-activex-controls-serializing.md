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
ms.openlocfilehash: c06299f2fc7409476e4f5e5744ea11c962e3b173
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621200"
---
# <a name="mfc-activex-controls-serializing"></a>Controles ActiveX MFC: Serializar

En este artículo se describe cómo serializar un control ActiveX. La serialización es el proceso de lectura o escritura en un medio de almacenamiento persistente, como un archivo de disco. La biblioteca de Microsoft Foundation Class (MFC) proporciona compatibilidad integrada para la serialización en la clase `CObject` . `COleControl`extiende esta compatibilidad a los controles ActiveX mediante el uso de un mecanismo de intercambio de propiedades.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

La serialización de controles ActiveX se implementa mediante la invalidación de [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange). Esta función, a la que se llama durante la carga y el guardado del objeto de control, almacena todas las propiedades implementadas con una variable miembro o una variable miembro con la notificación de cambios.

En los temas siguientes se tratan los principales problemas relacionados con la serialización de un control ActiveX:

- Implementar `DoPropExchange` la función para serializar el objeto de control

- [Personalizar el proceso de serialización](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementar la compatibilidad de versiones](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementar la función DoPropExchange

Cuando se usa el Asistente para controles ActiveX para generar el proyecto de control, se agregan automáticamente varias funciones de controlador predeterminadas a la clase de control, incluida la implementación predeterminada de [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange). En el ejemplo siguiente se muestra el código agregado a las clases creadas con el Asistente para controles ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Si desea que una propiedad sea persistente, modifique `DoPropExchange` agregando una llamada a la función de intercambio de propiedades. En el ejemplo siguiente se muestra la serialización de una propiedad CircleShape booleana personalizada, donde la propiedad CircleShape tiene un valor predeterminado de **true**:

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

En la tabla siguiente se enumeran las posibles funciones de intercambio de propiedades que puede utilizar para serializar las propiedades del control:

|Funciones de intercambio de propiedades|Propósito|
|---------------------------------|-------------|
|**PX_Blob ()**|Serializa una propiedad de datos de objeto binario grande (BLOB) de tipo.|
|**PX_Bool ()**|Serializa una propiedad booleana de tipo.|
|**PX_Color ()**|Serializa una propiedad de color de tipo.|
|**PX_Currency ()**|Serializa una propiedad de tipo **CY** (currency).|
|**PX_Double ()**|Serializa una propiedad **Double** de tipo.|
|**PX_Font ()**|Serializa una propiedad de tipo de fuente.|
|**PX_Float ()**|Serializa una propiedad de tipo **float** .|
|**PX_IUnknown ()**|Serializa una propiedad de tipo `LPUNKNOWN` .|
|**PX_Long ()**|Serializa una propiedad de tipo **Long** .|
|**PX_Picture ()**|Serializa una propiedad de imagen de tipo.|
|**PX_Short ()**|Serializa una propiedad de tipo **Short** .|
|**PXstring( )**|Serializa una propiedad de tipo `CString` .|
|**PX_ULong ()**|Serializa una propiedad de tipo **ULong** .|
|**PX_UShort ()**|Serializa una propiedad de tipo **USHORT** .|

Para obtener más información sobre estas funciones de intercambio de propiedades, vea [persistencia de controles OLE](reference/persistence-of-ole-controls.md) en la *referencia de MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Personalizar el comportamiento predeterminado de DoPropExchange

La implementación predeterminada de `DoPropertyExchange` (como se muestra en el tema anterior) realiza una llamada a la clase base `COleControl` . Esto serializa el conjunto de propiedades que admite automáticamente `COleControl` , que utiliza más espacio de almacenamiento que serializar solo las propiedades personalizadas del control. Al quitar esta llamada, el objeto solo podrá serializar las propiedades que considere importantes. Los Estados de las propiedades estándar que el control ha implementado no se serializarán al guardar o cargar el objeto de control a menos que agregue explícitamente **PX_** llamadas para ellos.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementar la compatibilidad de versiones

La compatibilidad de versiones permite que un control ActiveX revisado agregue nuevas propiedades persistentes, y que siga pudiendo detectar y cargar el estado persistente creado por una versión anterior del control. Para hacer que la versión de un control esté disponible como parte de sus datos persistentes, llame a [COleControl:: ExchangeVersion](reference/colecontrol-class.md#exchangeversion) en la función del control `DoPropExchange` . Esta llamada se inserta automáticamente si el control ActiveX se ha creado mediante el Asistente para controles ActiveX. Se puede quitar si no se necesita compatibilidad con la versión. Sin embargo, el costo en el tamaño del control es muy pequeño (4 bytes) para la flexibilidad agregada que proporciona la compatibilidad de versiones.

Si el control no se ha creado con el Asistente para controles ActiveX, agregue una llamada a `COleControl::ExchangeVersion` insertando la siguiente línea al principio de la `DoPropExchange` función (antes de la llamada a `COleControl::DoPropExchange` ):

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Puede usar cualquier **DWORD** como número de versión. Los proyectos generados por el Asistente para controles ActiveX usan `_wVerMinor` y `_wVerMajor` como valor predeterminado. Se trata de constantes globales definidas en el archivo de implementación de la clase de control ActiveX del proyecto. En el resto de la `DoPropExchange` función, puede llamar a [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion) en cualquier momento para recuperar la versión que está guardando o recuperando.

En el ejemplo siguiente, la versión 1 de este control de ejemplo tiene solo una propiedad "ReleaseDate". La versión 2 agrega una propiedad "OriginalDate". Si se indica al control que cargue el estado persistente de la versión anterior, inicializa la variable miembro para la nueva propiedad en un valor predeterminado.

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

De forma predeterminada, un control "convierte" los datos antiguos al formato más reciente. Por ejemplo, si la versión 2 de un control carga datos guardados por la versión 1, escribirá el formato de la versión 2 cuando se vuelva a guardar. Si desea que el control guarde los datos en el formato última lectura, pase **false** como tercer parámetro al llamar a `ExchangeVersion` . Este tercer parámetro es opcional y es **true** de forma predeterminada.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
