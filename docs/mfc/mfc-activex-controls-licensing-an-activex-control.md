---
title: "Controles ActiveX MFC: Licencias de un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "COleObjectFactory"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COleObjectFactory (clase), controles con licencia"
  - "GetLicenseKey (método)"
  - "otorgar licencias a controles ActiveX"
  - "controles ActiveX en MFC, otorgar licencias"
  - "VerifyLicenseKey (método)"
  - "VerifyUserLicense (método)"
ms.assetid: cacd9e45-701a-4a1f-8f1f-b0b39f6ac303
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Licencias de un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Compatibilidad de autorización, una característica opcional de controles ActiveX, permite controlar quién puede usar o distribuir el control. \(Para obtener una explicación adicional de los problemas de autorización, vea problemas de Licencias en [Actualizar un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md).\)  
  
 En este artículo se abordan los siguientes temas:  
  
-   [Información general del control ActiveX Licensing](#_core_overview_of_activex_control_licensing)  
  
-   [Crear un Control con licencia](#_core_creating_a_licensed_control)  
  
-   [Compatibilidad de autorización](#_core_licensing_support)  
  
-   [Personalizar el Licencias de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control)  
  
 Los controles ActiveX que implementan la autorización permiten, como programador de controles, determine cómo otras personas utilizarán el control ActiveX.  Se proporciona el comprador de control al control y el archivo de .LIC, con el contrato que el comprador puede distribuir el control, pero no el archivo de .LIC, con una aplicación que utiliza el control.  Esto impide que los usuarios de esa aplicación de nuevas aplicaciones de escritura que utilizan el control, sin primero la autorización de control del.  
  
##  <a name="_core_overview_of_activex_control_licensing"></a> Información general del control ActiveX Licensing  
 Para proporcionar compatibilidad con la autorización para los controles ActiveX, la clase de [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) proporciona una implementación de varias funciones de la interfaz de **IClassFactory2** : **IClassFactory2::RequestLicKey**, **IClassFactory2::GetLicInfo**, y **IClassFactory2::CreateInstanceLic**.  Cuando el desarrollador de aplicación contenedora realiza una solicitud para crear una instancia del control, una llamada a `GetLicInfo` se hace para comprobar que el archivo de control .LIC está presente.  Si el control es licencia, una instancia del control se puede crear y colocar en el contenedor.  Después de que el programador haya terminado de crear la aplicación contenedora, se realiza otra llamada de función, esta vez a `RequestLicKey`.  Esta función devuelve una clave de licencia \(una cadena de caracteres simple\) a la aplicación contenedora.  La clave devuelta se inserta en la aplicación.  
  
 La ilustración siguiente muestra la comprobación de la licencia de un control ActiveX que se utiliza durante el desarrollo de una aplicación contenedora.  Como se mencionó anteriormente, el desarrollador de aplicación contenedora debe tener el archivo adecuado de .LIC instalado en el equipo de desarrollo para crear una instancia del control.  
  
 ![Control ActiveX con licencia comprobado durante el desarrollo](../mfc/media/vc374d1.png "vc374D1")  
Comprobación de un control ActiveX con licencia durante el desarrollo  
  
 El proceso siguiente, que se muestra en la ilustración siguiente, se produce cuando el usuario final ejecuta la aplicación contenedora.  
  
 Cuando se inicia la aplicación, una instancia del control necesita normalmente crearse.  El contenedor consigue mediante una llamada a `CreateInstanceLic`, pasando la clave incrustada de licencia como parámetro.  Una comparación de cadenas se crea entre clave incrustada de licencia y copia de control la propia de la clave de licencia.  Si la coincidencia es correcta, se crea una instancia del control y la aplicación continúa ejecutándose normalmente.  Observe que el archivo de .LIC no necesita estar presente en el equipo del usuario del control.  
  
 ![Control ActiveX con licencia comprobado durante la ejecución](../mfc/media/vc374d2.png "vc374D2")  
Comprobación de un control ActiveX con licencia durante la ejecución  
  
 La autorización de Control consta de dos componentes básicos: código específico en la implementación DLL del control y el archivo de licencia.  El código se compone de dos \(o posiblemente tres\) llamadas de función y una cadena de caracteres, en lo sucesivo hace referencia como una “cadena de licencia”, que contiene un aviso de copyright.  Estas llamadas y la cadena de licencia se encuentran en el archivo de implementación del control \(.CPP\).  El archivo de licencia, generado por el asistente para controles ActiveX, es un archivo de texto con una instrucción de copyright.  Se realiza mediante el nombre de proyecto con extensión de .LIC, por ejemplo SAMPLE.LIC.  Un control con licencia se debe acompañado del archivo de licencia si el motor en tiempo de diseño es necesario.  
  
##  <a name="_core_creating_a_licensed_control"></a> Crear un Control con licencia  
 Cuando se utiliza el asistente para controles ActiveX para crear el marco del control, es fácil incluir compatibilidad de autorización.  Cuando se especifica que el control debe tener una licencia en tiempo de ejecución, el asistente para controles ActiveX agrega código a la clase de control para admitir la autorización.  El código se compone de funciones que utilizan una clave y un archivo de licencia para la comprobación de la licencia.  Estas funciones también se pueden modificar para personalizar la autorización del control.  Para obtener más información sobre la personalización de licencia, vea [Personalizar el Licencias de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control) más adelante en este artículo.  
  
#### Para agregar compatibilidad para autorizar con el asistente para controles ActiveX al crear el proyecto de control  
  
1.  Utilice las instrucciones en [Crear un control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md).  La página de **Configuración de la aplicación** del asistente para controles ActiveX contiene la opción de crear el control con licencia en tiempo de ejecución.  
  
 El asistente para controles ActiveX genera ahora un marco del control ActiveX que incluye la compatibilidad básica de autorización.  Para obtener una explicación detallada del código de la autorización, vea el tema siguiente.  
  
##  <a name="_core_licensing_support"></a> Compatibilidad de autorización  
 Cuando se utiliza el asistente para controles ActiveX para agregar compatibilidad de autorización para un control ActiveX, el asistente para controles ActiveX agrega código que declara e implementa la capacidad de autorización se agrega al encabezado del control y los archivos de implementación.  Este código se compone de una función miembro de `VerifyUserLicense` y una función miembro de `GetLicenseKey` , que reemplazan las implementaciones predeterminadas que se encuentran en [COleObjectFactory](../mfc/reference/coleobjectfactory-class.md) .  Estas funciones recuperan y active la licencia del control.  
  
> [!NOTE]
>  Una tercera función miembro, `VerifyLicenseKey` no es generada por el asistente para controles ActiveX, pero se puede reemplazar para personalizar el comportamiento de la comprobación de la clave de licencia.  
  
 Estas funciones miembro son:  
  
-   [VerifyUserLicense](../Topic/COleObjectFactory::VerifyUserLicense.md)  
  
     Comprueba que el control permite uso en tiempo de diseño al sistema para la presencia del archivo de licencia del control.  Llama a esta función por el marco como parte de procesar **IClassFactory2::GetLicInfo** y **IClassFactory::CreateInstanceLic**.  
  
-   [GetLicenseKey](../Topic/COleObjectFactory::GetLicenseKey.md)  
  
     Solicita una clave única del control DLL.  Esta clave se inserta en la aplicación contenedora y después se usa, junto con `VerifyLicenseKey`, para crear una instancia del control.  Llama a esta función por el marco como parte de procesar **IClassFactory2::RequestLicKey**.  
  
-   [VerifyLicenseKey](../Topic/COleObjectFactory::VerifyLicenseKey.md)  
  
     Comprueba que la clave incrustada y la clave única del control sean iguales.  Esto permite que el contenedor cree una instancia del control para su uso.  Llama a esta función por el marco como parte de procesar **IClassFactory2::CreateInstanceLic** y se puede reemplazar para proporcionar la comprobación personalizada de la clave de licencia.  La implementación predeterminada realiza una comparación de cadenas.  Para obtener más información, vea [Personalizar el Licencias de un control ActiveX](#_core_customizing_the_licensing_of_an_activex_control), más adelante en este artículo.  
  
###  <a name="_core_header_file_modifications"></a> Las modificaciones del archivo de encabezado  
 El asistente para controles ActiveX coloca el código siguiente en el archivo de encabezado del control.  En este ejemplo, dos funciones miembro del objeto `factory` de `CSampleCtrl` se declaran, uno que compruebe la presencia del archivo del control .LIC y otro que recupere la clave de licencia que se utilizará en la aplicación que contiene el control:  
  
 [!code-cpp[NVC_MFC_AxUI#39](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_1.h)]  
  
###  <a name="_core_implementation_file_modifications"></a> Modificaciones del archivo de implementación  
 El asistente para controles ActiveX coloca las dos instrucciones siguientes en el archivo de implementación del control para declarar el nombre de archivo de licencia y la cadena de licencia:  
  
 [!code-cpp[NVC_MFC_AxUI#40](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_2.cpp)]  
  
> [!NOTE]
>  Si modifica **szLicString** de cualquier forma, también debe modificar la primera línea del archivo de control .LIC o autorizando no funcionará correctamente.  
  
 El asistente para controles ActiveX coloca el código siguiente en el archivo de implementación del control para definir funciones de `VerifyUserLicense` y de `GetLicenseKey` de las clases de control:  
  
 [!code-cpp[NVC_MFC_AxUI#41](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_3.cpp)]  
  
 Finalmente, **ActiveX Control Wizard** modifica el archivo de proyecto de control .IDL.  La palabra clave de **licensed** se agrega a la declaración de coclass del control, como en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFC_AxUI#42](../mfc/codesnippet/CPP/mfc-activex-controls-licensing-an-activex-control_4.idl)]  
  
##  <a name="_core_customizing_the_licensing_of_an_activex_control"></a> Personalizar el Licencias de un control ActiveX  
 Dado que se declaran `VerifyUserLicense`, `GetLicenseKey`, y `VerifyLicenseKey` como virtual las funciones miembro de la clase de generador de controles, se pueden personalizar el comportamiento de autorización del control.  
  
 Por ejemplo, puede proporcionar varios niveles de autorización para el control reemplazando las funciones miembro de `VerifyUserLicense` o de `VerifyLicenseKey` .  En esta función puede ajustar las propiedades o métodos se exponen al usuario según el nivel de licencia que detectó.  
  
 También puede agregar código a la función de `VerifyLicenseKey` que proporciona un método personalizado para informar al usuario que controla la creación se ha producido un error.  Por ejemplo, en la función miembro de `VerifyLicenseKey` podría mostrar un cuadro de mensaje que decía que el control podría no para inicializar y por qué.  
  
> [!NOTE]
>  Otra manera de personalizar la comprobación de la licencia de controles ActiveX es comprobar la base de datos de registro de una clave del Registro específica, en lugar de llamar a `AfxVerifyLicFile`.  Para obtener un ejemplo de implementación predeterminada, vea la sección de [Modificaciones del archivo de implementación](#_core_implementation_file_modifications) de este artículo.  
  
 Para ver una explicación más problemas de autorización, vea problemas de Licencias en [Actualizar un control ActiveX existente](../mfc/upgrading-an-existing-activex-control.md).  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)   
 [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)