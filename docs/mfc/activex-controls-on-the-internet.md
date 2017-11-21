---
title: Controles ActiveX en Internet | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
caps.latest.revision: "14"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2b883e5f46e274c19b3e5c4ed3ae2698cef694e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="activex-controls-on-the-internet"></a>Controles ActiveX en Internet
Los controles ActiveX son la versión actualizada de la especificación de control OLE. Los controles son una arquitectura principal para desarrollar componentes de software programables que pueden utilizarse en una variedad de distintos contenedores, incluidos los exploradores Web compatibles con COM en Internet. Cualquier control de ActiveX puede ser un control de Internet y puede agregar su funcionalidad a un documento activo o formar parte de una página Web. Controles de una página Web pueden comunicarse entre sí mediante secuencias de comandos.  
  
 Controles ActiveX no se limitan a Internet. También se puede utilizar un control ActiveX en cualquier contenedor, siempre y cuando el control es compatible con las interfaces requeridas por dicho contenedor.  
  
 **Los controles ActiveX tienen varias ventajas, incluyendo:**  
  
-   Falta menos interfaces que los controles OLE anteriores.  
  
-   La capacidad puede carecer de ventana y siempre en el contexto activo.  
  
 **Para ser un control ActiveX, un control debe:**  
  
-   Compatibilidad con la **IUnknown** interfaz.  
  
-   Ser un objeto COM.  
  
-   Exportar **DLLRegisterServer** y **DllRegisterServer**.  
  
-   Admitir interfaces adicionales según sea necesario para la funcionalidad.  
  
## <a name="making-your-existing-controls-internet-friendly"></a>Habilitar los controles existentes compatible con Internet  
 Diseñar un control que funcione bien en un entorno de Internet requiere tener en cuenta las velocidades de transmisión relativamente baja en Internet. Puede usar los controles existentes; Sin embargo, hay pasos que debe seguir para reducir el tamaño del código y las propiedades del control descargar de forma asincrónica.  
  
 Para mejorar el rendimiento de los controles, siga estas sugerencias sobre eficiencia:  
  
-   Implementar las técnicas descritas en el artículo [controles ActiveX: optimización](../mfc/mfc-activex-controls-optimization.md).  
  
-   Tenga en cuenta cómo se crea una instancia de un control.  
  
-   Ser asincrónico; no mantenga otros programas.  
  
-   Descargar datos en bloques pequeños.  
  
     Al descargar grandes flujos como mapas de bits o datos de vídeo, tener acceso a datos de un control asincrónico en cooperación con el contenedor. Recuperar los datos de forma incremental o progresiva, trabajando en cooperación con otros controles que también puedan estar recuperando datos. También podría descargarse código de forma asincrónica.  
  
-   Descargar código y las propiedades en segundo plano.  
  
-   Interfaz de usuario activa tan pronto como sea posible.  
  
-   Tenga en cuenta cómo se almacenan los datos persistentes, propiedades y datos de gran tamaño BLOBs (por ejemplo, datos de mapa de bits imagen o vídeo).  
  
     Controles con grandes cantidades de datos persistentes, como mapas de bits grandes o archivos AVI, requieren especial atención al método de descarga. Un documento o página puede se hacen visible tan pronto como sea posible y permitir al usuario interactuar con la página mientras controles recuperan los datos en segundo plano.  
  
-   Escribir rutinas eficientes para mantener el tamaño del código y tiempo de ejecución.  
  
     Controles de botón y etiqueta pequeños, con solo unos pocos bytes de datos persistentes, son adecuados para su uso en el entorno de Internet y funcionan bien dentro de los exploradores.  
  
-   Considere la posibilidad de progreso se comunica al contenedor.  
  
     Notificar al contenedor del progreso en la descarga asincrónica, incluso cuando el usuario puede empezar a interactuar con una página, y una vez completada la descarga. El contenedor puede mostrar el progreso (como el porcentaje completado) para el usuario.  
  
-   Tenga en cuenta cómo se registran los controles en el equipo cliente.  
  
## <a name="creating-a-new-activex-control"></a>Crear un nuevo Control ActiveX  
 Al crear un nuevo control mediante el Asistente para aplicaciones, puede habilitar la compatibilidad con monikers asincrónicos, así como otras optimizaciones. Para agregar compatibilidad para propiedades de control de descarga de forma asincrónica, siga estos pasos:  
  
#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Para crear el proyecto mediante el Asistente para controles de ActiveX de MFC  
  
1.  Haga clic en `New` en el **archivo** menú.  
  
2.  Seleccione **Asistente para controles ActiveX de MFC** desde Visual C++ proyectos y el nombre del proyecto.  
  
3.  En el **configuración del Control** página, seleccione **carga de forma asincrónica propiedades**. Al seleccionar esta opción configura la propiedad de estado listo y el evento de cambio de estado listo para usted.  
  
     También puede seleccionar otras optimizaciones, como **activación sin ventana**, que se describe en [controles ActiveX: optimización](../mfc/mfc-activex-controls-optimization.md).  
  
4.  Elija **finalizar** para crear el proyecto.  
  
#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Para crear una clase derivada de CDataPathProperty  
  
1.  Crear una clase derivada de `CDataPathProperty`.  
  
2.  En cada uno de los archivos de origen que contiene el archivo de encabezado para el control, agregue el archivo de encabezado para esta clase antes de él.  
  
3.  En esta clase, reemplace el método `OnDataAvailable`. Esta función se invoca siempre que los datos están disponibles para su presentación. Como datos deja de estar disponibles, se puede controlar cualquier forma que elija, por ejemplo presentando progresivamente.  
  
     En el fragmento de código siguiente es un ejemplo sencillo de presentación progresiva de datos en un control de edición. Tenga en cuenta el uso de marca **BSCF_FIRSTDATANOTIFICATION** para borrar el control de edición.  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]  
  
     Tenga en cuenta que se debe incluir AFXCMN. H para poder utilizar el `CListCtrl` clase.  
  
4.  Cuando el control del general cambia estado (por ejemplo, de carga a inicializado o usuario interactivo), llamada `COleControl::InternalSetReadyState`. Si el control tiene la propiedad de ruta de acceso de datos solo una, puede agregar código en **BSCF_LASTDATANOTIFICATION** para notificar el contenedor que la descarga ha finalizado. Por ejemplo:  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]  
  
5.  Reemplace `OnProgress`. En `OnProgress`, se pasa un número que muestra el intervalo máximo y un número que se muestra hasta qué punto a lo largo de la descarga actual es. Puede usar estos números para mostrar el estado, como porcentaje completado para el usuario.  
  
 El procedimiento siguiente agrega una propiedad al control para utilizar la clase recién derivada.  
  
#### <a name="to-add-a-property"></a>Para agregar una propiedad  
  
1.  En **vista de clases**, haga clic en la interfaz situada bajo el nodo de biblioteca y seleccione **agregar**, a continuación, **Agregar propiedad**. Esto iniciará el **Asistente para agregar propiedades**.  
  
2.  En el **Asistente para agregar propiedades**, seleccione la **métodos Get/Set** botón de radio, escriba la **nombre de la propiedad**, por ejemplo, EditControlText y seleccione BSTR como el **Tipo de propiedad**.  
  
3.  Haga clic en **Finalizar**.  
  
4.  Declare una variable de miembro de su `CDataPathProperty`-clase derivada a la clase del control ActiveX.  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/cpp/activex-controls-on-the-internet_3.h)]  
  
5.  Implemente el **Get/Set** métodos. Para **obtener**, devolver la cadena. Para `Set`, cargar la propiedad y llamar a `SetModifiedFlag`.  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]  
  
6.  En [DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange), agregue la siguiente línea:  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]  
  
7.  Invalidar [ResetData](../mfc/reference/cdatapathproperty-class.md#resetdata) para notificar a la propiedad que se va a restablecer su control mediante la adición de esta línea:  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]  
  
## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Decidir si se debe derivar de CDataPathProperty o de CCachedDataPathProperty  
 El ejemplo anterior describe los pasos necesarios para derivar la propiedad del control de `CDataPathProperty`. Se trata de una buena opción si va a descargar datos en tiempo real que cambian con frecuencia y que no es necesario mantener todos los datos, pero solo el valor actual. Un ejemplo es un control de cotización bursátil.  
  
 También puede derivar de `CCachedDataPathProperty`. En este caso, se almacena en caché los datos descargados en un archivo de memoria. Esto es una buena opción si tiene que conservar todos los datos descargados: por ejemplo, un control que muestra un mapa de bits de forma progresiva. En este caso, la clase tiene una variable de miembro que contiene los datos:  
  
 `CMemFile m_Cache;`  
  
 En la clase del control ActiveX, puede usar este archivo de memoria asignada en `OnDraw` para mostrar los datos. En el control ActiveX `CCachedDataPathProperty`-clase derivada, reemplace la función miembro `OnDataAvailable` e invalidar el control después de llamar a la implementación de la clase base.  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]  
  
## <a name="downloading-data-asynchronously-using-activex-controls"></a>Descarga de datos de forma asincrónica con controles ActiveX  
 Descarga de datos a través de una red debe realizarse asincrónicamente. La ventaja de hacerlo es que por lo que si se transfiere una gran cantidad de datos o si la conexión es lenta, el proceso de descarga no bloquea otros procesos en el cliente.  
  
 Monikers asincrónicos proporcionan una manera de descargar datos de forma asincrónica a través de una red. Una operación de lectura en un moniker asincrónico devuelve inmediatamente, incluso si no se ha completado la operación.  
  
 Por ejemplo, si solo 10 bytes disponibles y lectura se llama de forma asincrónica en un archivo de 1 KB, lectura no se bloquea, pero devuelve los 10 bytes disponibles actualmente.  
  
 Implementar [monikers asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md) mediante la `CAsyncMonikerFile` clase. Sin embargo, pueden utilizar los controles ActiveX la `CDataPathProperty` (clase), que se deriva de `CAsyncMonikerFile`, para ayudar a implementar propiedades de control asincrónico.  
  
 El ejemplo ASYNDOWN muestra cómo configurar un bucle asincrónico usando temporizadores para leer los datos. ASYNDOWN se describe en detalle en el artículo de Knowledge Base "HOWTO: AsyncDown muestra Asynchronous Data Download" (Q177244) y está disponible para su descarga desde Microsoft Download Center. (Para obtener más información acerca de cómo descargar archivos desde Microsoft Download Center, consulte el artículo "How to obtener Microsoft compatibilidad con archivos de Online Services" (Q119591) en Microsoft Knowledge Base.) Encontrará artículos de Knowledge Base en [http://support.microsoft.com/support](http://support.microsoft.com/support).  
  
 La técnica básica utilizada en ASYNDOWN consiste en establecer un temporizador en **CDataPathProperty:: ondataavailable** para indicar cuando los datos están disponibles. Cuando se recibe el mensaje de temporizador, la aplicación lee en bloques de 128 bytes de datos y llena un control de edición. Si los datos no están disponibles cuando se controla el mensaje de temporizador, el temporizador se ha desactivado. `OnDataAvailable`activa el temporizador si llegan más datos más adelante.  
  
## <a name="displaying-a-control-on-a-web-page"></a>Mostrar un Control en una página Web  
 Este es un ejemplo de una etiqueta de objeto y atributos para insertar un control en una página Web.  
  
 `<OBJECT`  
  
 `CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"`  
  
 `CODEBASE="/ie/download/activex/iechart.ocx"`  
  
 `ID=chart1`  
  
 `WIDTH=400`  
  
 `HEIGHT=200`  
  
 `ALIGN=center`  
  
 `HSPACE=0`  
  
 `VSPACE=0`  
  
 `>`  
  
 `<PARAM NAME="BackColor" value="#ffffff">`  
  
 `<PARAM NAME="ForeColor" value="#0000ff">`  
  
 `<PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt">`  
  
 `</OBJECT>`  
  
## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Actualizar un Control OLE existente para usar las nuevas características de Control ActiveX  
 Si el control OLE se creó con una versión de Visual C++ anterior a la 4.2, hay pasos que puede seguir para mejorar su rendimiento y mejorar su funcionalidad. Para obtener una explicación detallada de estos cambios, consulte [controles ActiveX: optimización](../mfc/mfc-activex-controls-optimization.md).  
  
 Si va a agregar compatibilidad con propiedades asincrónicas a un control existente, debe agregar la propiedad de estado listo y `ReadyStateChange` evento usted mismo. En el constructor para el control, agregue:  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]  
  
 Se actualizará el estado de preparado tal y como se descarga el código mediante una llamada a [COleControl:: InternalSetReadyState](../mfc/reference/colecontrol-class.md#internalsetreadystate). Podría llamar a un mismo lugar `InternalSetReadyState` procede el `OnProgress` la invalidación de `CDataPathProperty`-clase derivada.  
  

  
## <a name="see-also"></a>Vea también  
 [Tareas de programación de Internet MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

