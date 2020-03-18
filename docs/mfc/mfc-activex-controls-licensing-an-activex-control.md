---
title: 'Controles ActiveX MFC: Licencias de un control ActiveX'
ms.date: 11/19/2018
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
ms.openlocfilehash: b08abdc0e2c17cb61c0c6a14cd712ec32ea816bd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438020"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Controles ActiveX MFC: Licencias de un control ActiveX

La compatibilidad con licencias, una característica opcional de los controles ActiveX, permite controlar quién puede usar o distribuir el control. (Para obtener más información acerca de los problemas de licencias, vea problemas de licencias en la [actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md)).

> [!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

En este artículo se tratan los temas siguientes:

- [Información general sobre la licencia de controles ActiveX](#_core_overview_of_activex_control_licensing)

- [Creación de un control con licencia](#_core_creating_a_licensed_control)

- [Compatibilidad con licencias](#_core_licensing_support)

- [Personalización de la licencia de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Los controles ActiveX que implementan las licencias le permiten, como desarrollador del control, determinar cómo usarán otras personas el control ActiveX. Proporcione al comprador de control el control y. Archivo LIC, con el acuerdo de que el comprador puede distribuir el control, pero no el. Archivo LIC, con una aplicación que utiliza el control. Esto impide que los usuarios de esa aplicación escriban nuevas aplicaciones que utilicen el control, sin tener que concederle primero la licencia del control.

##  <a name="_core_overview_of_activex_control_licensing"></a>Información general sobre la licencia de controles ActiveX

Para proporcionar compatibilidad con la concesión de licencias para los controles ActiveX, la clase [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) proporciona una implementación para varias funciones en la interfaz `IClassFactory2`: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`y `IClassFactory2::CreateInstanceLic`. Cuando el desarrollador de aplicaciones contenedoras realiza una solicitud para crear una instancia del control, se realiza una llamada a `GetLicInfo` para comprobar que el control. El archivo LIC está presente. Si el control tiene licencia, se puede crear una instancia del control y colocarla en el contenedor. Una vez que el desarrollador ha terminado de crear la aplicación contenedora, se realiza otra llamada a una función, esta vez a `RequestLicKey`. Esta función devuelve una clave de licencia (una cadena de caracteres simple) a la aplicación contenedora. La clave devuelta se incrusta en la aplicación.

En la ilustración siguiente se muestra la comprobación de la licencia de un control ActiveX que se usará durante el desarrollo de una aplicación contenedora. Como se mencionó anteriormente, el desarrollador de aplicaciones contenedoras debe tener el correcto. Archivo LIC instalado en el equipo de desarrollo para crear una instancia del control.

![Control ActiveX con licencia comprobado en el desarrollo](../mfc/media/vc374d1.gif "Control ActiveX con licencia comprobado durante el desarrollo") <br/>
Comprobación de un control ActiveX con licencia durante el desarrollo

El siguiente proceso, que se muestra en la siguiente ilustración, se produce cuando el usuario final ejecuta la aplicación contenedora.

Cuando se inicia la aplicación, normalmente es necesario crear una instancia del control. Para ello, el contenedor realiza una llamada a `CreateInstanceLic`, pasando la clave de licencia insertada como un parámetro. Después, se realiza una comparación de cadenas entre la clave de licencia insertada y la propia copia del control de la clave de licencia. Si la coincidencia se realiza correctamente, se crea una instancia del control y la aplicación continúa ejecutándose con normalidad. Tenga en cuenta que. No es necesario que el archivo LIC esté presente en el equipo del usuario del control.

![Control ActiveX con licencia comprobado en ejecución](../mfc/media/vc374d2.gif "Control ActiveX con licencia comprobado durante la ejecución") <br/>
Comprobación de un control ActiveX con licencia durante la ejecución

La concesión de licencias de control consta de dos componentes básicos: código específico en el archivo DLL de implementación del control y el archivo de licencia. El código se compone de dos (o posiblemente tres) llamadas a función y una cadena de caracteres, que se conoce en adelante como "cadena de licencia", que contiene un aviso de propiedad intelectual. Estas llamadas y la cadena de licencia se encuentran en la implementación del control (. CPP). El archivo de licencia, generado por el Asistente para controles ActiveX, es un archivo de texto con una instrucción de copyright. Se denomina con el nombre del proyecto con un. Extensión de LIC, por ejemplo,. Internacional. Un control con licencia debe ir acompañado del archivo de licencia si es necesario el uso en tiempo de diseño.

##  <a name="_core_creating_a_licensed_control"></a>Creación de un control con licencia

Cuando se usa el Asistente para controles ActiveX para crear el marco de trabajo de control, es fácil incluir la compatibilidad con las licencias. Cuando se especifica que el control debe tener una licencia en tiempo de ejecución, el Asistente para controles ActiveX agrega código a la clase del control para admitir las licencias. El código consta de funciones que utilizan una clave y un archivo de licencia para la comprobación de la licencia. Estas funciones también se pueden modificar para personalizar las licencias de control. Para obtener más información sobre la personalización de licencias, vea [personalizar la licencia de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control) más adelante en este artículo.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Para agregar compatibilidad con las licencias con el Asistente para controles ActiveX al crear el proyecto de control

1. Siga las instrucciones que se indican en [crear un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). La página Configuración de la **aplicación** del Asistente para controles ActiveX contiene la opción de crear el control con la licencia en tiempo de ejecución.

Ahora, el Asistente para controles ActiveX genera un marco de control ActiveX que incluye la compatibilidad con licencias básicas. Para obtener una explicación detallada del código de licencia, vea el tema siguiente.

##  <a name="_core_licensing_support"></a>Compatibilidad con licencias

Cuando se utiliza el Asistente para controles ActiveX para agregar compatibilidad con la concesión de licencias a un control ActiveX, el Asistente para controles ActiveX agrega código que declara e implementa la funcionalidad de licencia que se agrega al encabezado de control y a los archivos de implementación. Este código se compone de una `VerifyUserLicense` función miembro y una `GetLicenseKey` función miembro, que invalidan las implementaciones predeterminadas que se encuentran en [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Estas funciones recuperan y comprueban la licencia de control.

> [!NOTE]
>  La tercera función miembro, `VerifyLicenseKey` no es generada por el Asistente para controles ActiveX, pero se puede invalidar para personalizar el comportamiento de comprobación de la clave de licencia.

Estas funciones miembro son:

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Comprueba que el control permite el uso en tiempo de diseño comprobando si el sistema tiene la presencia del archivo de licencia de control. El marco de trabajo llama a esta función como parte del procesamiento `IClassFactory2::GetLicInfo` y `IClassFactory::CreateInstanceLic`.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Solicita una clave única del archivo DLL de control. Esta clave se incrusta en la aplicación contenedora y se usa más adelante, junto con `VerifyLicenseKey`, para crear una instancia del control. El marco de trabajo llama a esta función como parte del procesamiento `IClassFactory2::RequestLicKey`.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Comprueba que la clave incrustada y la clave única del control son iguales. Esto permite que el contenedor cree una instancia del control para su uso. El marco de trabajo llama a esta función como parte del procesamiento `IClassFactory2::CreateInstanceLic` y se puede invalidar para proporcionar una comprobación personalizada de la clave de licencia. La implementación predeterminada realiza una comparación de cadenas. Para obtener más información, vea [personalizar la licencia de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control), más adelante en este artículo.

###  <a name="_core_header_file_modifications"></a>Modificaciones de archivos de encabezado

El Asistente para controles ActiveX coloca el siguiente código en el archivo de encabezado del control. En este ejemplo, se declaran dos funciones miembro de `factory` de objeto de `CSampleCtrl`, una que comprueba la presencia del control. Archivo LIC y otro que recupera la clave de licencia que se va a utilizar en la aplicación que contiene el control:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a>Modificaciones de archivos de implementación

El Asistente para controles ActiveX coloca las dos instrucciones siguientes en el archivo de implementación del control para declarar el nombre de licencia y la cadena de licencia:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Si modifica `szLicString` de cualquier manera, también debe modificar la primera línea del control. El archivo de LIC o las licencias no funcionarán correctamente.

El Asistente para controles ActiveX coloca el siguiente código en el archivo de implementación del control para definir la clase de control ' `VerifyUserLicense` y funciones de `GetLicenseKey`:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Por último, el **Asistente para controles ActiveX** modifica el proyecto de control. Archivo IDL. La palabra clave **licensed** se agrega a la declaración de coclase del control, como en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a>Personalización de la licencia de un control ActiveX

Dado que `VerifyUserLicense`, `GetLicenseKey`y `VerifyLicenseKey` se declaran como funciones miembro virtuales de la clase de generador de controles, puede personalizar el comportamiento de las licencias del control.

Por ejemplo, puede proporcionar varios niveles de licencias para el control invalidando las funciones miembro `VerifyUserLicense` o `VerifyLicenseKey`. Dentro de esta función, puede ajustar las propiedades o los métodos que se exponen al usuario según el nivel de licencia detectado.

También puede agregar código a la función `VerifyLicenseKey` que proporciona un método personalizado para informar al usuario de que se ha producido un error en la creación del control. Por ejemplo, en la función miembro de `VerifyLicenseKey` podría mostrar un cuadro de mensaje que indica que el control no se pudo inicializar y por qué.

> [!NOTE]
>  Otra manera de personalizar la comprobación de la licencia de controles ActiveX es comprobar la base de datos de registro para obtener una clave del registro específica, en lugar de llamar a `AfxVerifyLicFile`. Para obtener un ejemplo de la implementación predeterminada, consulte la sección [modificaciones del archivo de implementación](#_core_implementation_file_modifications) de este artículo.

Para obtener más información acerca de los problemas de licencias, vea problemas de licencias en la [actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)
