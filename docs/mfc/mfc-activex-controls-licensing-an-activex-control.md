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
ms.openlocfilehash: aaab4ae3bb13790784a66d53b41dbc3a7cdaec89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364613"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Controles ActiveX MFC: Licencias de un control ActiveX

La compatibilidad con licencias, una característica opcional de los controles ActiveX, le permite controlar quién puede usar o distribuir el control. (Para obtener más información sobre los problemas de licencias, consulte Problemas de licencias en [la actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md).)

> [!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

En este artículo se tratan los temas siguientes:

- [Descripción general de las licencias de control ActiveX](#_core_overview_of_activex_control_licensing)

- [Creación de un control con licencia](#_core_creating_a_licensed_control)

- [Soporte de licencias](#_core_licensing_support)

- [Personalización de la licencia de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Los controles ActiveX que implementan licencias le permiten, como desarrollador de controles, determinar cómo otras personas usarán el control ActiveX. Usted proporciona al comprador de control el control y . LIC, con el acuerdo de que el comprador puede distribuir el control, pero no el . LIC, con una aplicación que utiliza el control. Esto impide que los usuarios de esa aplicación escriban nuevas aplicaciones que usan el control, sin conceder primero primero licencias para el control.

## <a name="overview-of-activex-control-licensing"></a><a name="_core_overview_of_activex_control_licensing"></a>Descripción general de las licencias de control ActiveX

Para proporcionar compatibilidad con licencias para controles ActiveX, la clase [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) proporciona una implementación para varias funciones `IClassFactory2` de la `IClassFactory2::RequestLicKey`interfaz: , `IClassFactory2::GetLicInfo`, y `IClassFactory2::CreateInstanceLic`. Cuando el desarrollador de la aplicación contenedora realiza una `GetLicInfo` solicitud para crear una instancia del control, se realiza una llamada para comprobar que el control . LIC está presente. Si el control tiene licencia, se puede crear una instancia del control y colocarla en el contenedor. Una vez que el desarrollador ha terminado de construir `RequestLicKey`la aplicación contenedora, se realiza otra llamada de función, esta vez a , . Esta función devuelve una clave de licencia (una cadena de caracteres simple) a la aplicación contenedora. A continuación, la clave devuelta se incrusta en la aplicación.

La figura siguiente muestra la verificación de licencia de un control ActiveX que se usará durante el desarrollo de una aplicación contenedora. Como se mencionó anteriormente, el desarrollador de la aplicación contenedora debe tener el archivo . LIC instalado en el equipo de desarrollo para crear una instancia del control.

![Control ActiveX con licencia comprobado durante el desarrollo](../mfc/media/vc374d1.gif "Control ActiveX con licencia comprobado durante el desarrollo") <br/>
Comprobación de un control ActiveX con licencia durante el desarrollo

El siguiente proceso, que se muestra en la siguiente figura, se produce cuando el usuario final ejecuta la aplicación contenedora.

Cuando se inicia la aplicación, normalmente se debe crear una instancia del control. El contenedor logra esto realizando `CreateInstanceLic`una llamada a , pasando la clave de licencia incrustada como parámetro. A continuación, se realiza una comparación de cadenas entre la clave de licencia incrustada y la propia copia del control de la clave de licencia. Si la coincidencia se realiza correctamente, se crea una instancia del control y la aplicación continúa ejecutándose normalmente. Tenga en cuenta que el archivo . No es necesario que el archivo LIC esté presente en el equipo del usuario de control.

![Control ActiveX con licencia comprobado durante la ejecución](../mfc/media/vc374d2.gif "Control ActiveX con licencia comprobado durante la ejecución") <br/>
Comprobación de un control ActiveX con licencia durante la ejecución

Las licencias de control constan de dos componentes básicos: código específico en el archivo DLL de implementación de control y el archivo de licencia. El código se compone de dos (o posiblemente tres) llamadas de función y una cadena de caracteres, en lo sucesivo denominada "cadena de licencia", que contiene un aviso de copyright. Estas llamadas y la cadena de licencia se encuentran en la implementación del control (. CPP). El archivo de licencia, generado por el Asistente para control ActiveX, es un archivo de texto con una declaración de copyright. Se denomina mediante el nombre del proyecto con un archivo . LIC, por ejemplo SAMPLE. Lic. Un control con licencia debe ir acompañado del archivo de licencia si se necesita un uso en tiempo de diseño.

## <a name="creating-a-licensed-control"></a><a name="_core_creating_a_licensed_control"></a>Creación de un control con licencia

Cuando se usa el Asistente para controles ActiveX para crear el marco de control, es fácil incluir compatibilidad con licencias. Cuando se especifica que el control debe tener una licencia en tiempo de ejecución, el Asistente para controles ActiveX agrega código a la clase de control para admitir licencias. El código consta de funciones que utilizan una clave y un archivo de licencia para la verificación de licencias. Estas funciones también se pueden modificar para personalizar las licencias de control. Para obtener más información sobre la personalización de licencias, consulte [Personalización de las licencias de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control) más adelante en este artículo.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Para agregar compatibilidad con licencias con el Asistente para control ActiveX al crear el proyecto de control

1. Utilice las instrucciones de Creación de [un control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). La página **Configuración** de la aplicación del Asistente para controles ActiveX contiene la opción de crear el control con la licencia en tiempo de ejecución.

El Asistente para controles ActiveX ahora genera un marco de control ActiveX que incluye compatibilidad básica con licencias. Para obtener una explicación detallada del código de licencia, consulte el tema siguiente.

## <a name="licensing-support"></a><a name="_core_licensing_support"></a>Soporte de licencias

Cuando se usa el Asistente para controles ActiveX para agregar compatibilidad con licencias a un control ActiveX, el Asistente para controles ActiveX agrega código que declara e implementa la capacidad de licencia se agrega al encabezado del control y a los archivos de implementación. Este código se `VerifyUserLicense` compone de `GetLicenseKey` una función miembro y una función miembro, que invalidan las implementaciones predeterminadas que se encuentran en [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Estas funciones recuperan y verifican la licencia de control.

> [!NOTE]
> Una tercera función miembro no `VerifyLicenseKey` la genera el Asistente para control ActiveX, pero se puede invalidar para personalizar el comportamiento de verificación de clave de licencia.

Estas funciones miembro son:

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Comprueba que el control permite el uso en tiempo de diseño comprobando el sistema para detectar la presencia del archivo de licencia de control. El marco de trabajo llama a `IClassFactory2::GetLicInfo` `IClassFactory::CreateInstanceLic`esta función como parte del procesamiento y .

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Solicita una clave única del archivo DLL de control. Esta clave se incrusta en la aplicación contenedora `VerifyLicenseKey`y se usa más adelante, junto con , para crear una instancia del control. El marco de trabajo llama a `IClassFactory2::RequestLicKey`esta función como parte del procesamiento.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Comprueba que la clave incrustada y la clave única del control son las mismas. Esto permite que el contenedor cree una instancia del control para su uso. El marco de trabajo llama a `IClassFactory2::CreateInstanceLic` esta función como parte del procesamiento y se puede invalidar para proporcionar una verificación personalizada de la clave de licencia. La implementación predeterminada realiza una comparación de cadenas. Para obtener más información, consulte [Personalización de la licencia de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control), más adelante en este artículo.

### <a name="header-file-modifications"></a><a name="_core_header_file_modifications"></a>Modificaciones del archivo de encabezado

El Asistente para controles ActiveX coloca el código siguiente en el archivo de encabezado del control. En este ejemplo, se `CSampleCtrl`declaran `factory` dos funciones miembro de 's object, una que comprueba la presencia del control . LIC y otro que recupera la clave de licencia que se utilizará en la aplicación que contiene el control:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

### <a name="implementation-file-modifications"></a><a name="_core_implementation_file_modifications"></a>Modificaciones del archivo de implementación

El Asistente para controles ActiveX coloca las dos instrucciones siguientes en el archivo de implementación del control para declarar el nombre de archivo de licencia y la cadena de licencia:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
> Si modifica `szLicString` de alguna manera, también debe modificar la primera línea del control. Lic o licencia no funcionarán correctamente.

El Asistente para controles ActiveX coloca el código siguiente en `VerifyUserLicense` `GetLicenseKey` el archivo de implementación del control para definir las funciones y la clase de control:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Por último, el **Asistente para controles ActiveX** modifica el proyecto de control. IDL. La palabra clave **licensed** se agrega a la declaración de coclase del control, como en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

## <a name="customizing-the-licensing-of-an-activex-control"></a><a name="_core_customizing_the_licensing_of_an_activex_control"></a>Personalización de la licencia de un control ActiveX

Dado `VerifyUserLicense` `GetLicenseKey`que `VerifyLicenseKey` , , y se declaran como funciones miembro virtuales de la clase de generador de control, puede personalizar el comportamiento de licencia del control.

Por ejemplo, puede proporcionar varios niveles de licencia `VerifyUserLicense` para `VerifyLicenseKey` el control reemplazando las funciones miembro o. Dentro de esta función puede ajustar qué propiedades o métodos se exponen al usuario de acuerdo con el nivel de licencia que detectó.

También puede agregar código `VerifyLicenseKey` a la función que proporciona un método personalizado para informar al usuario de que se ha producido un error en la creación del control. Por ejemplo, `VerifyLicenseKey` en la función miembro puede mostrar un cuadro de mensaje que indica que el control no se pudo inicializar y por qué.

> [!NOTE]
> Otra forma de personalizar la verificación de la licencia de control ActiveX es comprobar la base de datos de registro para una clave de registro específica, en lugar de llamar a `AfxVerifyLicFile`. Para obtener un ejemplo de la implementación predeterminada, vea la sección Modificaciones del archivo de [implementación](#_core_implementation_file_modifications) de este artículo.

Para obtener más información sobre los problemas de licencias, consulte Problemas de licencias en [la actualización de un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)
