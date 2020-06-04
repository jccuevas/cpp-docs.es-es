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
ms.openlocfilehash: 987cde2117307cdb5940a31e6f01efb15c527b84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364594"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Controles ActiveX MFC: Localizar un control ActiveX

En este artículo se describen los procedimientos para localizar interfaces de control ActiveX.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Si desea adaptar un control ActiveX a un mercado internacional, es posible que desee localizar el control. Windows admite muchos idiomas además del inglés predeterminado, incluido el alemán, el francés y el sueco. Esto puede presentar problemas para el control si su interfaz está en inglés solamente.

En general, los controles ActiveX siempre deben basar su configuración regional en la propiedad LocaleID ambiente. Hay tres formas de hacerlo:

- Cargar recursos, siempre a petición, en función del valor actual de la propiedad LocaleID ambiente. El ejemplo de controles ActiveX de MFC [LOCALIZE](../overview/visual-cpp-samples.md) utiliza esta estrategia.

- Cargue los recursos cuando se forme una instancia del primer control, en función de la propiedad LocaleID ambiente, y use estos recursos para todas las demás instancias. En este artículo se muestra esta estrategia.

    > [!NOTE]
    >  Esto no funcionará correctamente en algunos casos, si las instancias futuras tienen configuraciones regionales diferentes.

- Utilice `OnAmbientChanged` la función de notificación para cargar dinámicamente los recursos adecuados para la configuración regional del contenedor.

    > [!NOTE]
    >  Esto funcionará para el control, pero el archivo DLL en tiempo de ejecución no actualizará dinámicamente sus propios recursos cuando cambie la propiedad LocaleID ambiente. Además, los archivos DLL en tiempo de ejecución para controles ActiveX usan la configuración regional del subproceso para determinar la configuración regional de sus recursos.

El resto de este artículo describe dos estrategias de localización. La primera estrategia [localiza la interfaz de programación del control](#_core_localizing_your_control.92.s_programmability_interface) (nombres de propiedades, métodos y eventos). La segunda estrategia [localiza la interfaz de usuario del control,](#_core_localizing_the_control.92.s_user_interface)mediante la propiedad LocaleID del entorno del contenedor. Para obtener una demostración de la localización de controles, vea el ejemplo de controles ActiveX de MFC [LOCALIZE](../overview/visual-cpp-samples.md).

## <a name="localizing-the-controls-programmability-interface"></a><a name="_core_localizing_your_control.92.s_programmability_interface"></a>Localización de la interfaz de programación del control

Al localizar la interfaz de programación del control (la interfaz utilizada por los programadores que escriben aplicaciones que utilizan el control), debe crear una versión modificada del control. IDL (un script para crear la biblioteca de tipos de control) para cada idioma que desee admitir. Este es el único lugar que necesita para localizar los nombres de propiedad del control.

Cuando desarrolle un control localizado, incluya el identificador de configuración regional como atributo en el nivel de biblioteca de tipos. Por ejemplo, si desea proporcionar una biblioteca de tipos con nombres de propiedad localizados en francés, haga una copia de la SAMPLE. IDL y llámelo SAMPLEFR. Idl. Agregue un atributo de ID de configuración regional al archivo (el identificador de configuración regional para francés es 0x040c), similar al siguiente:

[!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]

Cambie los nombres de propiedad en SAMPLEFR. IDL a sus equivalentes en francés y, a continuación, utilice MKTYPLIB. EXE para producir la biblioteca de tipos francesa, SAMPLEFR. Tlb.

Para crear varias bibliotecas de tipos localizadas, puede agregar cualquier archivo . IDL al proyecto y se compilarán automáticamente.

#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Para agregar un archivo . IDL a su proyecto de control ActiveX

1. Con el proyecto de control abierto, en el menú **Proyecto,** haga clic en **Agregar elemento existente**.

   Aparece el cuadro de diálogo **Agregar elemento existente.**

1. Si es necesario, seleccione la unidad y el directorio que desea ver.

1. En el cuadro **Tipo de** archivo, seleccione Todos los archivos **(\*\*. )**.

1. En el cuadro de lista de archivos, haga doble clic en el archivo . IDL que desea insertar en el proyecto.

1. Haga clic en **Abrir** cuando haya agregado todo lo necesario . Archivos IDL.

Dado que los archivos se han agregado al proyecto, se compilarán cuando se compila el resto del proyecto. Las bibliotecas de tipos localizadas se encuentran en el directorio de proyecto de control ActiveX actual.

Dentro del código, los nombres de propiedad internos (normalmente en inglés) siempre se usan y nunca se localizan. Esto incluye el mapa de distribución de controles, las funciones de intercambio de propiedades y el código de intercambio de datos de la página de propiedades.

Sólo una biblioteca de tipos (. TLB) puede enlazarse a los recursos de la implementación del control (. OCX). Esta suele ser la versión con los nombres estandarizados (normalmente, en inglés). Para enviar una versión localizada de su control que necesita para enviar el archivo . OCX (que ya se ha enlazado al valor predeterminado. TLB) y el archivo . TLB para la configuración regional adecuada. Esto significa que sólo el archivo . OCX es necesario para las versiones en inglés, ya que el archivo . TLB ya ha estado vinculado a él. Para otras configuraciones regionales, la biblioteca de tipos localizada también debe enviarse con el archivo . Ocx.

Para asegurarse de que los clientes del control pueden encontrar la biblioteca de tipos localizada, registre la configuración regional específica. TLB en la sección TypeLib del registro del sistema de Windows. El tercer parámetro (normalmente opcional) de la función [AfxOleRegisterTypeLib](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) se proporciona para este propósito. En el ejemplo siguiente se registra una biblioteca de tipos en francés para un control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]

Cuando se registra el `AfxOleRegisterTypeLib` control, la función busca automáticamente el archivo . TLB en el mismo directorio que el control y lo registra en la base de datos de registro de Windows. Si el archivo . No se encuentra el archivo TLB, la función no tiene ningún efecto.

## <a name="localizing-the-controls-user-interface"></a><a name="_core_localizing_the_control.92.s_user_interface"></a>Localización de la interfaz de usuario del control

Para localizar la interfaz de usuario de un control, coloque todos los recursos visibles del usuario del control (como páginas de propiedades y mensajes de error) en archivos DLL de recursos específicos del idioma. A continuación, puede usar la propiedad LocaleID de ambiente del contenedor para seleccionar el archivo DLL adecuado para la configuración regional del usuario.

En el ejemplo de código siguiente se muestra un enfoque para buscar y cargar el archivo DLL de recursos para una configuración regional específica. Esta función `GetLocalizedResourceHandle` miembro, llamada para este ejemplo, puede ser una función miembro de la clase de control ActiveX:

[!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]

Tenga en cuenta que el identificador de sublenguaje se puede comprobar en cada caso de la instrucción switch, para proporcionar una localización más especializada. Para obtener una demostración `GetResourceHandle` de esta función, vea la función en el ejemplo de controles ActiveX de MFC [LOCALIZE](../overview/visual-cpp-samples.md).

Cuando el control se carga por primera vez en un contenedor, puede llamar a [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) para recuperar el identificador de configuración regional. A continuación, el control puede pasar `GetLocalizedResourceHandle` el valor de identificador de configuración regional devuelto a la función, que carga la biblioteca de recursos adecuada. El control debe pasar el identificador resultante, si existe, a [AfxSetResourceHandle](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):

[!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]

Coloque el ejemplo de código anterior en una función miembro del control, como una invalidación de [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Además, *m_hResDLL* debe ser una variable miembro de la clase de control.

Puede usar una lógica similar para localizar la página de propiedades de un control. Para localizar la página de propiedades, agregue código similar al siguiente ejemplo al archivo de implementación de la página de propiedades (en una invalidación de [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):

[!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
