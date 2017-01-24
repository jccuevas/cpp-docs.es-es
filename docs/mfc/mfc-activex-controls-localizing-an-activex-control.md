---
title: "Controles ActiveX MFC: Localizar un control ActiveX | Microsoft Docs"
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
  - "LocaleID"
  - "AfxOleRegisterTypeLib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LocaleID ambient (propiedad)"
  - "adaptación, controles ActiveX"
  - "LOCALIZE (ejemplo) [MFC]"
  - "controles ActiveX en MFC, adaptar"
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
caps.latest.revision: 12
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controles ActiveX MFC: Localizar un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se abordan los procedimientos para buscar interfaces de controles ActiveX.  
  
 Si desea adaptar un control ActiveX a un mercado internacional, quizás desee buscar el control.  Windows admite muchos idiomas además del inglés predeterminado, incluidas alemán, francés, y sueco.  Esto puede mostrar los problemas del control si la interfaz se encuentra en inglés únicamente.  
  
 Los controles ActiveX deben basar normalmente siempre la configuración regional en la propiedad de ambiente de LocaleID.  Existen tres formas de hacer esto:  
  
-   Cargue los recursos, siempre a petición, en función del valor actual de la propiedad de ambiente de LocaleID.  El ejemplo de controles ActiveX de MFC [LOCALIZE](../top/visual-cpp-samples.md) utiliza esta estrategia.  
  
-   Cargue los recursos cuando el primer control se cita como ejemplo, en función de la propiedad de ambiente de LocaleID, y utiliza estos recursos para el resto de las instancias.  Este artículo muestra esta estrategia.  
  
    > [!NOTE]
    >  Esto no funcionará correctamente en algunos casos, si las instancias futuras tienen distintas configuraciones regionales.  
  
-   Utilice la función de notificación de **OnAmbientChanged** para cargar dinámicamente los recursos apropiados para la configuración regional del contenedor.  
  
    > [!NOTE]
    >  Esto funcionará para el control, pero el tiempo de ejecución DLL no actualizará dinámicamente a los recursos propios cuando los cambios de propiedad de ambiente de LocaleID.  Además, los archivos DLL en tiempo de ejecución para los controles ActiveX utilizan la configuración regional del subproceso para determinar la configuración regional para los recursos.  
  
 El resto de este artículo se describe dos estrategias que encuentran.  La primera estrategia [busque la interfaz de programación de control](#_core_localizing_your_control.92.s_programmability_interface) \(nombres de propiedades, métodos, y eventos\).  La segunda estrategia [busque la interfaz de usuario del control](#_core_localizing_the_control.92.s_user_interface), utilizando la propiedad de ambiente de LocaleID del contenedor.  Para obtener una demostración de localización de control, vea el ejemplo de controles ActiveX de MFC [LOCALIZE](../top/visual-cpp-samples.md).  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Encontrar la interfaz Programmability de Control  
 Al encontrar la interfaz de programación del control \(interfaz utilizada por los programadores que escriben las aplicaciones que utilizan el control\), debe crear una versión modificada del archivo del control .IDL \(un script para compilar la biblioteca de tipos de control\) para cada idioma piensa admitir.  Éste es el único cambio que necesita adaptar los nombres de propiedad del control.  
  
 Al desarrollar un control localizado, incluya el identificador de configuración regional como atributo en el nivel de la biblioteca de tipos.  Por ejemplo, si desea proporcionar una biblioteca de tipos con nombres de propiedad localizados francés, haga una copia del archivo de SAMPLE.IDL, y denomínela SAMPLEFR.IDL.  Agregue un atributo id de configuración regional al archivo \(el identificador de configuración regional de francés es 0x040c\), similar al siguiente:  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 Cambie los nombres de propiedad en SAMPLEFR.IDL a sus equivalentes en francés, y utilice MKTYPLIB.EXE para generar la biblioteca de tipos en francés, SAMPLEFR.TLB.  
  
 Para crear las bibliotecas de tipos localizadas varias puede agregar cualquier archivo traducido de .IDL al proyecto y compilan automáticamente.  
  
#### Para agregar un archivo de .IDL al proyecto de control ActiveX  
  
1.  Con el proyecto de control abierto, en el menú de **Project** , haga clic en **Agregar elemento existente**.  
  
     El cuadro de diálogo de **Agregar elemento existente** aparece.  
  
2.  Si es necesario, seleccione la unidad y el directorio para ver.  
  
3.  En el cuadro de **Tipo de archivo** , seleccione **Todos los archivos \(\*.\*\)**.  
  
4.  En el cuadro de lista de archivos, haga doble clic en el archivo de .IDL que desea incrustar en el proyecto.  
  
5.  Haga clic en **Abierta** cuando ha agregado todos los archivos de .IDL.  
  
 Dado que los archivos se han agregado al proyecto, se compilarán cuando el resto del proyecto se compila.  Las bibliotecas de tipos localizadas se encuentran en el directorio actual del proyecto de control ActiveX.  
  
 Dentro del código, los nombres de propiedad internos \(normalmente en inglés\) siempre se utilizan y nunca se encuentran.  Esto incluye el mapa de envío del control, las funciones de intercambio de propiedad, y el código de intercambio de datos de la página de propiedades.  
  
 Sólo un archivo de biblioteca de tipos \(.TLB\) se puede enlazar en los recursos del archivo de implementación del control \(.OCX\).  Suele ser la versión con \(normalmente, inglés\) los nombres normalizados.  Para distribuir una versión localizada del control que necesita enviar el .OCX \(que ya se ha enlazado a la versión del valor predeterminado .TLB\) y el .TLB para la correspondiente.  Esto significa que sólo el .OCX es necesario para las versiones en inglés, ya que el .TLB correcto ya se ha enlazado a él.  Para configuraciones regionales, la biblioteca de tipos localizada también debe enviarse con el .OCX.  
  
 Para garantizar que los clientes del control puedan encontrar la biblioteca de tipos adaptada, registre los archivos configuración regional\- específicos de .TLB bajo la sección de Tipos de registro del sistema de Windows.  El tercer parámetro normalmente opcional\) de la función de [AfxOleRegisterTypeLib](../Topic/AfxOleRegisterTypeLib.md) se proporciona con este fin.  El ejemplo siguiente se registra una biblioteca de tipos en francés para un control ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 Cuando se registra el control, la función de `AfxOleRegisterTypeLib` busca automáticamente el archivo especificado de .TLB en el mismo directorio que el control y lo registra en la base de datos del registro de Windows.  Si el archivo de .TLB no se encuentra, la función no tiene ningún efecto.  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Encontrar la interfaz de usuario del Control  
 Para encontrar la interfaz de usuario de un control, sitúe los recursos usuario\- visible del control \(como páginas de propiedades y mensajes de error\) en un archivo DLL de recursos específicas del idioma.  A continuación puede utilizar la propiedad de ambiente de LocaleID de contenedor para seleccionar DLL apropiado para la configuración regional del usuario.  
  
 El ejemplo de código siguiente muestra un enfoque para buscar y cargar el archivo DLL de recursos para una configuración regional específica.  Esta función miembro, denominada `GetLocalizedResourceHandle` para este ejemplo, puede ser una función miembro de una clase de control ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 Observe que el identificador de variante se puede proteger cada caso de la instrucción switch, para proporcionar una localización especializada.  Para obtener una demostración de esta función, vea la función de `GetResourceHandle` en el ejemplo de controles ActiveX de MFC [LOCALIZE](../top/visual-cpp-samples.md).  
  
 Cuando el control primero se carga en un contenedor, puede llamar a [COleControl::AmbientLocaleID](../Topic/COleControl::AmbientLocaleID.md) para recuperar el identificador de la configuración regional  El control puede pasar el valor devuelto del identificador de configuración regional a la función de `GetLocalizedResourceHandle` , que carga la biblioteca de recursos adecuada.  El control debe pasar el identificador resultante, si existe, a [AfxSetResourceHandle](../Topic/AfxSetResourceHandle.md):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 Coloque el ejemplo de código anterior en una función miembro del control, como un reemplazo de [COleControl::OnSetClientSite](../Topic/COleControl::OnSetClientSite.md).  Además, `m_hResDLL` debe ser una variable miembro de la clase de control.  
  
 Puede utilizar una lógica similar para encontrar la página de propiedades de un control.  Para encontrar la página de propiedades, agregue el código de ejemplo siguiente al archivo de aplicación de la página de propiedades \(en un reemplazo de [COlePropertyPage::OnSetPageSite](../Topic/COlePropertyPage::OnSetPageSite.md)\):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/CPP/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)