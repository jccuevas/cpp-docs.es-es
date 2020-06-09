---
title: 'Controles ActiveX MFC: Localizar un control ActiveX'
ms.date: 09/12/2018
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
ms.openlocfilehash: a85ec5cbed797b756afd93cd8423c58d138a0625
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615419"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Controles ActiveX MFC: Localizar un control ActiveX

En este artículo se describen los procedimientos para localizar interfaces de control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Si desea adaptar un control ActiveX a un mercado internacional, puede que desee localizar el control. Windows admite muchos idiomas además del inglés predeterminado, como alemán, francés y sueco. Esto puede presentar problemas para el control si su interfaz solo está en inglés.

En general, los controles ActiveX siempre deben basar su configuración regional en la propiedad LocaleID ambiente. Hay tres formas de hacerlo:

- Cargar recursos, siempre a petición, en función del valor actual de la propiedad ambiente LocaleID. La [configuración regional](../overview/visual-cpp-samples.md) de los controles ActiveX de MFC utiliza esta estrategia.

- Cargue los recursos cuando se haya instancia del primer control, en función de la propiedad LocaleID ambiente, y use estos recursos para todas las demás instancias. En este artículo se muestra esta estrategia.

    > [!NOTE]
    >  Esto no funcionará correctamente en algunos casos, si las instancias futuras tienen diferentes configuraciones regionales.

- Utilice la `OnAmbientChanged` función de notificación para cargar dinámicamente los recursos adecuados para la configuración regional del contenedor.

    > [!NOTE]
    >  Esto funcionará para el control, pero el archivo DLL en tiempo de ejecución no actualizará dinámicamente sus propios recursos cuando cambie la propiedad LocaleID ambiente. Además, los archivos dll en tiempo de ejecución para los controles ActiveX usan la configuración regional del subproceso para determinar la configuración regional de sus recursos.

En el resto de este artículo se describen dos estrategias de localización. La primera estrategia [localiza la interfaz de programación del control](#_core_localizing_your_control.92.s_programmability_interface) (nombres de propiedades, métodos y eventos). La segunda estrategia [localiza la interfaz de usuario del control](#_core_localizing_the_control.92.s_user_interface)mediante la propiedad ambiente LocaleID del contenedor. Para ver una demostración de la localización de controles, vea la [configuración regional](../overview/visual-cpp-samples.md)de los controles ActiveX de MFC.

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Localizar la interfaz de programación del control

Al localizar la interfaz de programación del control (la interfaz utilizada por los programadores que escriben las aplicaciones que utilizan el control), debe crear una versión modificada del control. Archivo IDL (un script para compilar la biblioteca de tipos de control) para cada lenguaje que desee admitir. Este es el único lugar que necesita para localizar los nombres de las propiedades del control.

Al desarrollar un control localizado, incluya el identificador de configuración regional como un atributo en el nivel de la biblioteca de tipos. Por ejemplo, si desea proporcionar una biblioteca de tipos con nombres de propiedad localizados en francés, haga una copia de su ejemplo. Archivo IDL y llámelo SAMPLEFR. IDL. Agregue un atributo de ID. de configuración regional al archivo (el ID. de configuración regional para francés es 0x040c), similar al siguiente:

[!code-cpp[NVC_MFC_AxLoc#1](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Cambie los nombres de propiedad en SAMPLEFR. IDL a sus equivalentes en francés y, a continuación, use MKTYPLIB. EXE para generar la biblioteca de tipos de francés, SAMPLEFR. TLB.

Para crear varias bibliotecas de tipos localizadas, puede agregar cualquier localizada. Archivos IDL para el proyecto y se generarán automáticamente.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Para agregar un. Archivo IDL al proyecto de control ActiveX

1. Con el proyecto de control abierto, en el menú **proyecto** , haga clic en **Agregar elemento existente**.

   Aparece el cuadro de diálogo **Agregar elemento existente**.

1. Si es necesario, seleccione la unidad y el directorio que desea ver.

1. En el cuadro **archivos de tipo** , seleccione **todos los archivos ( \* . \* )**.

1. En el cuadro de lista archivo, haga doble clic en el. Archivo IDL que desea insertar en el proyecto.

1. Haga clic en **abrir** cuando haya agregado todos los necesarios. Archivos IDL.

Dado que los archivos se han agregado al proyecto, se compilarán cuando se compile el resto del proyecto. Las bibliotecas de tipos localizadas se encuentran en el directorio actual del proyecto de control ActiveX.

En el código, los nombres de propiedad internos (normalmente en inglés) siempre se usan y nunca se localizan. Esto incluye el mapa de envío de control, las funciones de intercambio de propiedades y el código de intercambio de datos de la página de propiedades.

Solo una biblioteca de tipos (. TLB) se puede enlazar a los recursos de la implementación del control (. OCX). Esta suele ser la versión con los nombres normalizados (normalmente, en inglés). Para enviar una versión localizada del control, debe enviar el. OCX (que ya se ha enlazado al valor predeterminado). La versión de TLB) y. TLB para la configuración regional adecuada. Esto significa que solo el. OCX es necesario para las versiones en inglés, desde el correcto. TLB ya está enlazado a él. En el caso de otras configuraciones regionales, la biblioteca de tipos localizada también debe enviarse con. OCX.

Para asegurarse de que los clientes del control pueden encontrar la biblioteca de tipos localizada, registre la configuración regional específica. Archivos TLB en la sección TypeLib del registro del sistema de Windows. Para este propósito, se proporciona el tercer parámetro (normalmente opcional) de la función [AfxOleRegisterTypeLib](reference/registering-ole-controls.md#afxoleregistertypelib) . En el ejemplo siguiente se registra una biblioteca de tipos en francés para un control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Cuando se registra el control, la `AfxOleRegisterTypeLib` función busca automáticamente el especificado. Archivo TLB en el mismo directorio que el control y lo registra en la base de datos de registro de Windows. Si el. No se encuentra el archivo TLB, la función no tiene ningún efecto.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Localizar la interfaz de usuario del control

Para localizar la interfaz de usuario de un control, coloque todos los recursos visibles para el usuario del control (como páginas de propiedades y mensajes de error) en archivos dll de recursos específicos del lenguaje. A continuación, puede usar la propiedad ambiente LocaleID del contenedor para seleccionar el archivo DLL adecuado para la configuración regional del usuario.

En el ejemplo de código siguiente se muestra un enfoque para buscar y cargar el archivo DLL de recursos para una configuración regional específica. Esta función miembro, a la `GetLocalizedResourceHandle` que se llama en este ejemplo, puede ser una función miembro de la clase de control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Tenga en cuenta que el identificador de subidioma se podría comprobar en cada caso de la instrucción switch para proporcionar una localización más especializada. Para ver una demostración de esta función, vea la `GetResourceHandle` función en la [configuración regional](../overview/visual-cpp-samples.md)de los controles ActiveX de MFC.

Cuando el control se carga por primera vez en un contenedor, puede llamar a [COleControl:: AmbientLocaleID](reference/colecontrol-class.md#ambientlocaleid) para recuperar el ID. de configuración regional. A continuación, el control puede pasar el valor de ID. de configuración regional devuelto a la `GetLocalizedResourceHandle` función, que carga la biblioteca de recursos adecuada. El control debe pasar el identificador resultante, si existe, a [AfxSetResourceHandle](reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Coloque el ejemplo de código anterior en una función miembro del control, como una invalidación de [COleControl:: OnSetClientSite](reference/colecontrol-class.md#onsetclientsite). Además, *m_hResDLL* debe ser una variable miembro de la clase control.

Puede usar una lógica similar para localizar la página de propiedades de un control. Para localizar la página de propiedades, agregue código similar al siguiente ejemplo al archivo de implementación de la página de propiedades (en una invalidación de [COlePropertyPage:: OnSetPageSite](reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
