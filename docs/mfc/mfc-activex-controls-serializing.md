---
title: 'Controles ActiveX MFC: Serializar | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f9db6ff6c0cdda01875e4968e4d92ca087ad2b57
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930066"
---
# <a name="mfc-activex-controls-serializing"></a>Controles ActiveX MFC: Serializar
Este artículo describe cómo serializar un control ActiveX. La serialización es el proceso de leer o escribir en un medio de almacenamiento persistente, como un archivo de disco. La biblioteca (Microsoft Foundation Classes) proporciona compatibilidad integrada para la serialización en la clase `CObject`. `COleControl` extiende esta compatibilidad a controles ActiveX mediante el uso de un mecanismo de intercambio de la propiedad.  
  
 Serialización para controles ActiveX se implementa mediante la invalidación [COleControl:: DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Esta función, se llama durante la carga y guardar del objeto de control, almacena todas las propiedades implementadas con una variable de miembro o una variable miembro con notificación de cambio.  
  
 Los siguientes temas abordan los principales problemas relacionados con la serialización de un control ActiveX:  
  
-   Implementar `DoPropExchange` función para serializar el objeto de control  
  
-   [Personalizar el proceso de serialización](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [Implementar la compatibilidad de versión](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> Implementar la función DoPropExchange  
 Cuando utiliza el Asistente para controles ActiveX para generar el proyecto de control, varias funciones de controlador de forma predeterminada se agregan automáticamente a la clase de control, incluida la implementación predeterminada de [COleControl:: DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). En el ejemplo siguiente se muestra el código agregado a las clases creadas con el Asistente para controles ActiveX:  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]  
  
 Si desea hacer que una propiedad sea persistente, modifique `DoPropExchange` mediante la adición de una llamada a la función de cambio de propiedad. En el ejemplo siguiente se muestra la serialización de una propiedad personalizada de tipo Boolean, donde la propiedad CircleShape tiene un valor predeterminado de **TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]  
  
 En la tabla siguiente se enumera las funciones de intercambio de propiedad posibles que puede utilizar para serializar las propiedades del control:  
  
|Funciones de intercambio de propiedad|Propósito|  
|---------------------------------|-------------|  
|**(De PX_Blob)**|Serializa un tipo de propiedad de datos de objetos binarios grandes (BLOB).|  
|**(De PX_Bool)**|Serializa una propiedad de tipo Boolean.|  
|**(De PX_Color)**|Serializa una propiedad de color de tipo.|  
|**(De PX_Currency)**|Serializa un tipo **CY** propiedad (moneda).|  
|**(De PX_Double)**|Serializa un tipo **doble** propiedad.|  
|**(De PX_Font)**|Serializa una propiedad de tipo de fuente.|  
|**(De PX_Float)**|Serializa un tipo **float** propiedad.|  
|**(De PX_IUnknown)**|Serializa una propiedad de tipo `LPUNKNOWN`.|  
|**(De PX_Long)**|Serializa un tipo **largo** propiedad.|  
|**(De PX_Picture)**|Serializa un tipo de propiedad de imagen.|  
|**(De PX_Short)**|Serializa un tipo **corto** propiedad.|  
|**(De PXstring)**|Serializa un tipo `CString` propiedad.|  
|**(De PX_ULong)**|Serializa un tipo **ULONG** propiedad.|  
|**(De PX_UShort)**|Serializa un tipo **USHORT** propiedad.|  
  
 Para obtener más información sobre estas funciones de intercambio de propiedad, vea [persistencia de controles OLE](../mfc/reference/persistence-of-ole-controls.md) en el *referencia de MFC*.  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Personalizar el comportamiento predeterminado de DoPropExchange  
 La implementación predeterminada de `DoPropertyExchange` (como se muestra en el tema anterior) realiza una llamada a la clase base `COleControl`. Serializa el conjunto de propiedades admitidas automáticamente por `COleControl`, que utiliza más espacio de almacenamiento que serializar sólo las propiedades personalizadas del control. La eliminación de esta llamada, permite el objeto serializar sólo las propiedades que considere importantes. Los Estados de propiedad estándar ha implementado el control no se serializará al guardar o cargar el objeto de control a menos que agregue explícitamente **PX_** llama para ellos.  
  
##  <a name="_core_implementing_version_support"></a> Implementar la compatibilidad de versión  
 Compatibilidad de versiones permite un control ActiveX revisado agregar nuevas propiedades persistentes y seguir siendo capaces de detectar y cargar el estado persistente creado por una versión anterior del control. Para que la versión de un control esté disponible como parte de sus datos persistentes, llame a [COleControl:: ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) en el control `DoPropExchange` (función). Esta llamada se inserta automáticamente si el control ActiveX se creó mediante el Asistente para controles ActiveX. Se puede quitar si no es necesaria la compatibilidad de versiones. Sin embargo, el costo de tamaño del control es muy pequeño (4 bytes) para la flexibilidad adicional que proporciona compatibilidad con la versión.  
  
 Si el control no se creó con el Asistente para controles ActiveX, agregue una llamada a `COleControl::ExchangeVersion` insertando la siguiente línea al principio de su `DoPropExchange` función (antes de llamar a `COleControl::DoPropExchange`):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 Puede usar cualquier **DWORD** como el número de versión. Los proyectos generados por el Asistente para controles ActiveX utilizan `_wVerMinor` y `_wVerMajor` como el valor predeterminado. Se trata de constantes globales definidas en el archivo de implementación de la clase del control ActiveX del proyecto. En el resto de su `DoPropExchange` función, puede llamar a [CPropExchange:: GetVersion](../mfc/reference/cpropexchange-class.md#getversion) en cualquier momento para recuperar la versión que se va a guardar o recuperar.  
  
 En el ejemplo siguiente, la versión 1 de este control de ejemplo tiene sólo una propiedad "ReleaseDate". Versión 2 agrega una propiedad "OriginalDate". Si el control se le solicita que cargue el estado persistente de la versión anterior, inicializa la variable miembro para la nueva propiedad en un valor predeterminado.  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 De forma predeterminada, un control "convierte" datos antiguos en el formato más reciente. Por ejemplo, si la versión 2 de un control de carga los datos que se guardan con la versión 1, escribirá el formato de versión 2 cuando se guarda de nuevo. Si desea que el control para guardar los datos en la última lectura de formato, pase **FALSE** como tercer parámetro al llamar a `ExchangeVersion`. Este tercer parámetro es opcional y es **TRUE** de forma predeterminada.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

