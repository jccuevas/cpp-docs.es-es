---
title: 'Controles ActiveX MFC: Licencias de un Control de ActiveX | Microsoft Docs'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COleObjectFactory
dev_langs:
- C++
helpviewer_keywords:
- COleObjectFactory class [MFC], licensing controls
- MFC ActiveX controls [MFC], licensing
- VerifyLicenseKey method [MFC]
- VerifyUserLicense method [MFC]
- GetLicenseKey method [MFC]
- licensing ActiveX controls
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b66debe5c6401b4eee01bc81acc58b8445e20c21
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50068780"
---
# <a name="mfc-activex-controls-licensing-an-activex-control"></a>Controles ActiveX MFC: Licencias de un control ActiveX

Las licencias de soporte técnico, una característica opcional de controles ActiveX, le permite controlar quién puede usar o distribuir el control. (Para obtener más información sobre problemas de licencias, consulte los problemas de licencias en [actualizar un ActiveX Control existente](../mfc/upgrading-an-existing-activex-control.md).)

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

En este artículo se trata los temas siguientes:

- [Información general de la licencia de controles ActiveX](#_core_overview_of_activex_control_licensing)

- [Creación de un Control con licencia](#_core_creating_a_licensed_control)

- [Concesión de licencia](#_core_licensing_support)

- [Personalizar la licencia de un Control ActiveX](#_core_customizing_the_licensing_of_an_activex_control)

Controles ActiveX que implementan las licencias, permiten que el desarrollador del control, para determinar cómo otras personas utilizan el control ActiveX. Proporcione el comprador de control con el control y. LIC, con el acuerdo que podrá distribuir el control, pero no el. LIC, con una aplicación que utiliza el control. Esto impide que los usuarios de la aplicación desde la escritura de nuevas aplicaciones que usan el control, sin la primera licencia el control del usuario.

##  <a name="_core_overview_of_activex_control_licensing"></a> Información general de la licencia de controles ActiveX

Para proporcionar compatibilidad con las licencias para los controles ActiveX, el [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) clase proporciona una implementación de varias funciones en el `IClassFactory2` interfaz: `IClassFactory2::RequestLicKey`, `IClassFactory2::GetLicInfo`, y `IClassFactory2::CreateInstanceLic`. Cuando el desarrollador de aplicaciones de contenedor realiza una solicitud para crear una instancia del control, una llamada a `GetLicInfo` se realiza para comprobar que el control. Archivo LIC está presente. Si el control tiene licencia, una instancia del control puede crear y se coloca en el contenedor. Después de que el desarrollador ha terminado de construir la aplicación contenedora, llamar otra función, esta vez para `RequestLicKey`, se realiza. Esta función devuelve una clave de licencia (una cadena de caracteres simple) a la aplicación contenedora. La clave devuelta se incrusta en la aplicación.

La siguiente ilustración muestra la comprobación de licencia de un control ActiveX que se usará durante el desarrollo de una aplicación contenedora. Como se mencionó anteriormente, el desarrollador de aplicaciones de contenedor debe tener el archivo. LIC correcto instalado en el equipo de desarrollo para crear una instancia del control.

![Con licencia comprobado durante el desarrollo de controles de ActiveX](../mfc/media/vc374d1.gif "vc374d1") comprobación de un Control de ActiveX con licencia durante el desarrollo

El proceso siguiente, que se muestra en la ilustración siguiente, se produce cuando el usuario final se ejecuta la aplicación contenedora.

Cuando se inicia la aplicación, normalmente debe crearse una instancia del control. El contenedor realiza mediante una llamada a `CreateInstanceLic`, pasando la clave de licencia incrustado como un parámetro. A continuación, se realiza una comparación de cadenas entre la clave de licencia incrustada y la copia del control de la clave de licencia. Si la coincidencia es correcta, se crea una instancia del control y la aplicación continúa ejecutándose normalmente. Tenga en cuenta que el. Archivo LIC no necesita estar presente en el equipo del usuario de control.

![Con licencia comprobado durante la ejecución de control de ActiveX](../mfc/media/vc374d2.gif "vc374d2") comprobación de un Control de ActiveX con licencia durante la ejecución

Licencias de control consta de dos componentes básicos: código específico en el archivo DLL de implementación del control y el archivo de licencia. El código se compone de dos (o posiblemente tres) llamadas de función y una cadena de caracteres, en lo sucesivo denominado una "cadena de licencia", que contiene un aviso de copyright. Estas llamadas y la cadena de licencia se encuentran en la implementación del control (. Archivo CPP). El archivo de licencia, generado por el Asistente para controles ActiveX, es un archivo de texto con una instrucción de copyright. Se denomina con el nombre del proyecto con un. Extensión LIC, por ejemplo, ejemplo. LIC. Un control con licencia debe ir acompañado por el archivo de licencia, si se necesita tiempo de diseño.

##  <a name="_core_creating_a_licensed_control"></a> Creación de un Control con licencia

Cuando usa el Asistente para controles ActiveX para crear el marco de control, es fácil incluyen licencias de soporte técnico. Cuando se especifica que el control debe tener una licencia de tiempo de ejecución, el Asistente para controles ActiveX agrega código a la clase de control para admitir licencias. El código consta de las funciones que usan un archivo de claves y licencias para la comprobación de licencia. Estas funciones también se pueden modificar para personalizar la licencia del control. Para obtener más información sobre la personalización de la licencia, consulte [personalizar la licencia de un ActiveX Control](#_core_customizing_the_licensing_of_an_activex_control) más adelante en este artículo.

#### <a name="to-add-support-for-licensing-with-the-activex-control-wizard-when-you-create-your-control-project"></a>Para agregar compatibilidad con las licencias con el Asistente para controles ActiveX al crear el proyecto de control

1. Siga las instrucciones de [crear un ActiveX Control de MFC](../mfc/reference/creating-an-mfc-activex-control.md). El **configuración de la aplicación** página del Asistente de Control ActiveX contiene la opción para crear el control con la licencia en tiempo de ejecución.

El Asistente para controles ActiveX genera ahora un control ActiveX que incluye compatibilidad básica con la licencia. Para obtener una explicación detallada del código de licencia, vea el tema siguiente.

##  <a name="_core_licensing_support"></a> Concesión de licencia

Cuando usa el Asistente para controles ActiveX para agregar compatibilidad con licencia a un control ActiveX, el Asistente para controles ActiveX agrega código que declara e implementa la funcionalidad de licencias se agrega al encabezado de control y la implementación los archivos. Este código se compone de un `VerifyUserLicense` función miembro y un `GetLicenseKey` función miembro, que reemplazan las implementaciones predeterminadas que se encuentra en [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) . Estas funciones se recupere y comprobación la licencia del control.

> [!NOTE]
>  Una tercera función miembro, `VerifyLicenseKey` no generado por el Asistente para controles ActiveX, pero se puede invalidar para personalizar el comportamiento de la comprobación de las claves de licencia.

Estas funciones miembro son:

- [VerifyUserLicense](../mfc/reference/coleobjectfactory-class.md#verifyuserlicense)

   Comprueba que el control permite el uso de tiempo de diseño mediante la comprobación del sistema para detectar la presencia del archivo de licencia del control. Esta función se llama el marco de trabajo como parte del procesamiento `IClassFactory2::GetLicInfo` y `IClassFactory::CreateInstanceLic`.

- [GetLicenseKey](../mfc/reference/coleobjectfactory-class.md#getlicensekey)

   Solicita una clave única de la DLL de control. Esta clave está incrustada en la aplicación de contenedor y usará más adelante, junto con `VerifyLicenseKey`, para crear una instancia del control. Esta función se llama el marco de trabajo como parte del procesamiento `IClassFactory2::RequestLicKey`.

- [VerifyLicenseKey](../mfc/reference/coleobjectfactory-class.md#verifylicensekey)

   Comprueba que la clave incrustada y la clave única del control son los mismos. Esto permite que el contenedor crear una instancia del control para su uso. Esta función se llama el marco de trabajo como parte del procesamiento `IClassFactory2::CreateInstanceLic` y se puede invalidar para proporcionar una verificación personalizada de la clave de licencia. La implementación predeterminada realiza una comparación de cadenas. Para obtener más información, consulte [personalizar la licencia de un ActiveX Control](#_core_customizing_the_licensing_of_an_activex_control), más adelante en este artículo.

###  <a name="_core_header_file_modifications"></a> Modificaciones de archivos de encabezado

El Asistente para controles ActiveX se coloca el código siguiente en el archivo de encabezado. En este ejemplo, dos funciones miembro de `CSampleCtrl`del objeto `factory` se declaran, que comprueba la presencia del control. Archivo LIC y otra que recupera la clave de licencia para su uso en la aplicación que contiene el control:

[!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_1.h)]

###  <a name="_core_implementation_file_modifications"></a> Modificaciones de archivos de implementación

El Asistente para controles ActiveX coloca las dos instrucciones siguientes en el archivo de implementación para declarar el nombre de archivo de licencia y la cadena de licencia:

[!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_2.cpp)]

> [!NOTE]
>  Si modifica `szLicString` de cualquier manera, también debe modificar la primera línea en el control. Archivo LIC o licencias no funcionarán correctamente.

El Asistente para controles ActiveX se coloca el código siguiente en el archivo de implementación para definir la clase de control `VerifyUserLicense` y `GetLicenseKey` funciones:

[!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_3.cpp)]

Por último, el **Asistente para controles ActiveX** modifica el proyecto de control. Archivo IDL. El **licencia** palabra clave se agrega a la declaración de coclass del control, como en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/cpp/mfc-activex-controls-licensing-an-activex-control_4.idl)]

##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Personalizar la licencia de un Control ActiveX

Dado que `VerifyUserLicense`, `GetLicenseKey`, y `VerifyLicenseKey` se declaran como funciones miembro virtuales de la clase de generador de control, puede personalizar el comportamiento del control licencias.

Por ejemplo, puede proporcionar varios niveles de licencia para el control invalidando el `VerifyUserLicense` o `VerifyLicenseKey` funciones miembro. Dentro de esta función se puede ajustar qué métodos o propiedades se exponen al usuario según el nivel de licencia detectado.

También puede agregar código a la `VerifyLicenseKey` función que proporciona un método personalizado para informar al usuario que controlan la creación ha producido un error. Por ejemplo, en su `VerifyLicenseKey` cuadro de función miembro puede mostrar un mensaje que indica que no se pudo inicializar el control y por qué.

> [!NOTE]
>  Otra forma de personalizar la comprobación de licencia del control ActiveX es comprobar la base de datos de registro para una clave del Registro específica, en lugar de llamar `AfxVerifyLicFile`. Para obtener un ejemplo de la implementación predeterminada, vea el [las modificaciones de archivos de implementación](#_core_implementation_file_modifications) sección de este artículo.

Para obtener más información sobre problemas de licencias, consulte los problemas de licencias en [actualizar un ActiveX Control existente](../mfc/upgrading-an-existing-activex-control.md).

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)

