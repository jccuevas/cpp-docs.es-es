---
title: 'Controles ActiveX MFC: Localizar un Control ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2705061b1914ac8fad9f7ca8d769df16bab2f5c1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415699"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Controles ActiveX MFC: Localizar un control ActiveX

En este artículo se describe procedimientos para la localización de las interfaces del control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Si desea adaptar un control ActiveX en un mercado internacional, desea localizar el control. Windows admite muchos idiomas además del inglés, incluidos alemán, francés y sueco predeterminado. Esto puede suponer problemas para el control si su interfaz sólo está en inglés.

En general, los controles ActiveX siempre deben basar su configuración regional en la propiedad de ambiente LocaleID. Existen tres formas de hacer esto:

- Cargar los recursos, siempre a petición, según el valor actual de la propiedad de ambiente LocaleID. Ejemplo de los controles ActiveX de MFC [LOCALIZE](../visual-cpp-samples.md) usa esta estrategia.

- Cargar los recursos cuando se crea una instancia del primer control, en función de la propiedad de ambiente LocaleID y use estos recursos para todas las demás instancias. En este artículo se muestra esta estrategia.

    > [!NOTE]
    >  Esto no funcionará correctamente en algunos casos, si las instancias futuras con diferentes configuraciones regionales.

- Use el `OnAmbientChanged` función de notificación para cargar dinámicamente los recursos adecuados para la configuración regional del contenedor.

    > [!NOTE]
    >  Esto funcionará para el control, pero el archivo DLL de tiempo de ejecución no actualizará dinámicamente sus propios recursos cuando cambia la propiedad de ambiente LocaleID. Además, los archivos DLL de tiempo de ejecución para los controles ActiveX usan la configuración regional del subproceso para determinar la configuración regional para sus recursos.

El resto de este artículo describen dos estrategias de creación de versiones localizadas. La primera estrategia [localiza la interfaz de programación del control](#_core_localizing_your_control.92.s_programmability_interface) (nombres de propiedades, métodos y eventos). La segunda estrategia [localiza la interfaz de usuario del control](#_core_localizing_the_control.92.s_user_interface), mediante la propiedad de ambiente LocaleID del contenedor. Para ver una demostración de localización de control, vea el ejemplo de controles ActiveX MFC [LOCALIZE](../visual-cpp-samples.md).

##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Adaptar la interfaz de programación del Control

Al localizar la interfaz de programación del control (la interfaz utilizada por los programadores que escriben aplicaciones que usan el control), debe crear una versión modificada del control. IDL de archivos (una secuencia de comandos para la creación de la biblioteca de tipos de control) para cada idioma que desea admitir. Este es el único lugar que deberá adaptar los nombres de propiedad de control.

Al desarrollar un control adaptado, incluya el identificador de configuración regional como un atributo en el nivel de la biblioteca de tipos. Por ejemplo, si desea proporcionar una biblioteca de tipos con los nombres de propiedad traducida francés, realizar una copia de su ejemplo. IDL de archivo y llámelo SAMPLEFR. IDL. Agregar un atributo de Id. de configuración regional en el archivo (el identificador de configuración regional de francés es 0x040c), similar al siguiente:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Cambiar los nombres de propiedad en SAMPLEFR. IDL a sus equivalentes de francés y, a continuación, utilice MKTYPLIB. EXE para generar el francés biblioteca de tipos, SAMPLEFR. TLB.

Para crear varias bibliotecas de tipos traducida puede agregarlos archivos. Archivos IDL para el proyecto y se generarán automáticamente.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Para agregar una. Archivo IDL para el proyecto de control ActiveX

1. Con el proyecto de control abierto, en el **proyecto** menú, haga clic en **Agregar elemento existente**.

     El **Agregar elemento existente** aparece el cuadro de diálogo.

1. Si es necesario, seleccione la unidad y directorio que desea ver.

1. En el **archivos de tipo** cuadro, seleccione **todos los archivos (\*.\*)** .

1. En el cuadro de lista de archivos, haga doble clic en el. Archivo IDL que desea insertar en el proyecto.

1. Haga clic en **abierto** cuando haya agregado todas las necesarias. Archivos IDL.

Como los archivos se han agregado al proyecto, se generará cuando se compila el resto del proyecto. Las bibliotecas de tipos localizados se encuentran en el directorio actual del proyecto de control ActiveX.

Dentro del código, los nombres de propiedad interno (normalmente en inglés) siempre se usan y nunca están localizados. Esto incluye el mapa de envíos del control, las funciones de intercambio de la propiedad y el código de intercambio de datos de página de propiedad.

Biblioteca de tipos solo una (. Archivo TLB) se puede enlazar a los recursos de la implementación del control (. Archivo OCX). Esto suele ser la versión con el estándar (normalmente, en inglés) los nombres. Para enviar una versión localizada del control se debe suministrar la. OCX (que ya se ha enlazado con el valor predeterminado. Versión TLB) y el. TLB para la configuración regional adecuada. Esto significa que solo el. OCX es necesaria para las versiones en inglés, desde el valor correcto. TLB ya se ha enlazado a él. Para otras configuraciones regionales, la biblioteca de tipos traducida también se debe enviar con el. OCX.

Para asegurarse de que los clientes de su control puedan encontrar la biblioteca de tipos traducida, registre la configuración regional específica. Tlb específicos en la sección de la biblioteca de tipos de registro del sistema de Windows. El tercer parámetro (normalmente opcional) de la [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) función se proporciona para este propósito. El ejemplo siguiente registra una biblioteca de tipos en francés para un control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Cuando se registra el control, el `AfxOleRegisterTypeLib` función busca automáticamente para el elemento especificado. Archivo TLB en el mismo directorio que el control y lo registra en la base de datos de registro de Windows. Si el. No se encuentra el archivo TLB, la función no tiene ningún efecto.

##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Adaptar la interfaz de usuario del Control

Para localizar la interfaz de usuario de un control, coloque todos los recursos del control visible para el usuario (por ejemplo, páginas de propiedades y los mensajes de error) en archivos DLL de recursos específicos del idioma. A continuación, puede usar la propiedad de ambiente LocaleID del contenedor para seleccionar el archivo DLL adecuado para la configuración regional del usuario.

En el ejemplo de código siguiente se muestra un enfoque para buscar y cargar la DLL de recursos para una configuración regional específica. Esta función miembro, denominada `GetLocalizedResourceHandle` en este ejemplo, puede ser una función miembro de la clase del control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Tenga en cuenta que el identificador de subidioma podría comprobarse en cada caso de la instrucción switch, para proporcionar una localización más especializado. Para ver una demostración de esta función, vea el `GetResourceHandle` ejemplo controla la función de ActiveX de MFC [LOCALIZE](../visual-cpp-samples.md).

Cuando el control se carga por primera vez en un contenedor, puede llamar a [COleControl:: AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) para recuperar el identificador de configuración regional. El control, a continuación, puede pasar el valor de identificador de configuración regional devuelto a la `GetLocalizedResourceHandle` función, que carga la biblioteca de recursos apropiado. El control debe pasar el identificador resultante, si hay alguno, a [AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Coloque el ejemplo de código anterior en una función miembro de control, como una invalidación de [COleControl:: OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Además, *m_hResDLL* debería ser una variable de miembro de la clase de control.

Puede utilizar una lógica similar para la localización de la página de propiedades de un control. Para localizar la página de propiedades, agregar código similar al siguiente ejemplo al archivo de implementación de la página de propiedad (en un reemplazo de [COlePropertyPage:: OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

