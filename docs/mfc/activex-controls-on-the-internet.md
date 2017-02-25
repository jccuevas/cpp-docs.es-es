---
title: "Controles ActiveX en Internet | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles ActiveX [C++], crear"
  - "controles ActiveX [C++], Internet"
  - "descargar datos con controles ActiveX"
  - "aplicaciones de Internet [C++], controles ActiveX"
  - "redes [C++], descargar con controles ActiveX"
  - "controles OLE [C++], actualizar a ActiveX"
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# Controles ActiveX en Internet
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles ActiveX son la versión actualizada de la especificación de controles activex.  Los Controles son una arquitectura principal para el desarrollo de componentes de software programables que se pueden utilizar en distintos contenedores, incluidos los exploradores web COM\- corriente en internet.  Cualquier control ActiveX puede ser un control de internet y puede agregar su funcionalidad a un documento activo o formar parte de una página Web.  Los Controles de una página Web pueden comunicarse entre sí mediante script.  
  
 Los controles ActiveX no se limitan a internet.  Un control ActiveX también se puede utilizar en cualquier contenedor, mientras el control admite las interfaces requeridas por ese contenedor.  
  
 **Los controles ActiveX tienen varias ventajas, como:**  
  
-   Menos interfaces necesarias que controles OLE anteriores.  
  
-   La capacidad de activa sin ventana y siempre en contexto.  
  
 **Para ser un control ActiveX, un control debe:**  
  
-   Admite la interfaz de **IUnknown** .  
  
-   Es un objeto COM.  
  
-   Exportación **DLLRegisterServer** y **DLLUnRegisterServer**.  
  
-   Interfaces adicionales admiten según sea necesario para la funcionalidad.  
  
## Crear Controles existentes Herramienta de creación de HTML\- fáciles de usar  
 El diseño de un control que funciona bien en un entorno de internet requiere la consideración para las tasas de transmisión relativamente poco en internet.  Puede utilizar los controles existentes; sin embargo, hay pasos que debe seguir para crear el tamaño de código más pequeño y para que las propiedades del control descargan de forma asincrónica.  
  
 Para mejorar el rendimiento de los controles, siga estas sugerencias en consideraciones de eficacia:  
  
-   Implemente las técnicas descritas en el caso [Controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md).  
  
-   Observe cómo se crea una instancia de un control.  
  
-   Es asincrónico; no compatibilidad con otros programas.  
  
-   Descargue los datos en pequeños bloques.  
  
     Al descargar secuencias grandes como mapas de bits o datos de vídeo, tenga acceso a los datos de un control de forma asincrónica en cooperación con el contenedor.  Recupere los datos de forma incremental o progresiva, trabajando de forma cooperativa con otros controles que pueden recuperar datos.  El código también puede descargar de forma asincrónica.  
  
-   Código y propiedades de descarga en segundo plano.  
  
-   Activo convertido de la interfaz de usuario lo más rápidamente posible.  
  
-   Observe cómo se almacenan los datos persistente, las propiedades y los objetos binarios grandes de datos \(como una imagen de mapa de bits o datos de vídeo\).  
  
     Controles con cantidades importantes de datos persistentes, como mapas de bits o archivos AVI grandes, requieren una atención cuidadosa a descargar método.  Un documento o una página puede volverse visible lo más rápidamente posible, y permite al usuario interactuar con la página como controles recuperan datos en segundo plano.  
  
-   Escriba las rutinas eficaces para limitar el tamaño y el tiempo de ejecución de código.  
  
     El botón pequeños y controles de etiqueta, con solo unos bytes de datos persistentes, son adecuados para su uso en el entorno de internet y funcionan bien dentro de los exploradores.  
  
-   Considere el progreso se comunica al contenedor.  
  
     Notifique al contenedor de progreso en la descarga asincrónica, incluso cuando el usuario puede iniciar para interactuar con una página y, cuando se completa la descarga.  El contenedor puede mostrar progreso \(como porcentaje completado\) al usuario.  
  
-   Observe cómo los controles están registradas en el equipo cliente.  
  
## Crear un control ActiveX New  
 Al crear un nuevo control mediante el Asistente para aplicaciones, puede habilitar la compatibilidad con los monikeres asincrónicos así como otras optimizaciones.  Para agregar compatibilidad para las propiedades del control de descarga asincrónica, siga estos pasos:  
  
#### Para crear el proyecto mediante el asistente para controles ActiveX MFC  
  
1.  Haga clic en `New` en el menú de **archivo** .  
  
2.  Seleccione **Asistente para controles ActiveX MFC** proyectos de Visual C\+\+ y asigne al proyecto.  
  
3.  En la página de **Configuración del control** , seleccione **Loads properties asynchronously**.  Activar esta opción configura la propiedad de estado lista y el evento de cambio de estado listo para usted.  
  
     También puede seleccionar otras optimizaciones, como **Windowless activation**, que se describe en [Controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md).  
  
4.  Elija **Finalizar** para crear el proyecto.  
  
#### Para crear una clase derivada CDataPathProperty  
  
1.  Cree una clase derivada de `CDataPathProperty`.  
  
2.  En cada uno de los archivos de código fuente que incluya el archivo de encabezado para el control, agregue el archivo de encabezado para esta clase antes de ella.  
  
3.  En esta clase, invalide `OnDataAvailable`.  Esta función se denomina siempre que los datos estén disponibles para la presentación.  Aunque los datos disponible, puede controlarlo cualquier forma que elija, por ejemplo progresivamente generandola.  
  
     El fragmento de código siguiente es un ejemplo simple progresivamente de mostrar datos en un control de edición.  Observe el uso de marcador **BSCF\_FIRSTDATANOTIFICATION** de desactivar el control de edición.  
  
     [!code-cpp[NVC_MFCActiveXControl#1](../mfc/codesnippet/CPP/activex-controls-on-the-internet_1.cpp)]  
  
     Tenga en cuenta que debe incluir AFXCMN.H para utilizar la clase de `CListCtrl` .  
  
4.  Cuando los cambios del estado de control \(por ejemplo, de carga a inicializado o de usuario interactivas\), llamada `COleControl::InternalSetReadyState`.  Si el control sólo tiene una propiedad de la ruta de acceso de datos, puede agregar código de **BSCF\_LASTDATANOTIFICATION** para notificar al contenedor de la descarga se completa.  Por ejemplo:  
  
     [!code-cpp[NVC_MFCActiveXControl#2](../mfc/codesnippet/CPP/activex-controls-on-the-internet_2.cpp)]  
  
5.  Reemplace `OnProgress`.  En `OnProgress`, se pasa un número que muestra el intervalo máximo y un número que muestran hasta qué punto a lo largo de descarga actual.  Puede utilizar estos números para mostrar el estado como porcentaje completado al usuario.  
  
 El procedimiento siguiente se agrega una propiedad al control para utilizar la clase simplemente derivada.  
  
#### Para agregar una propiedad  
  
1.  En **vista de clases**, haga clic con el botón secundario en la interfaz bajo el nodo de biblioteca y **Add**seleccione, a continuación **Agregar propiedad**.  Esto iniciará **Asistente para agregar propiedades**.  
  
2.  En **Asistente para agregar propiedades**, seleccione el botón de opción de **Set\/Get Methods** , escriba **Nombre de propiedad**, por ejemplo, EditControlText, y BSTR seleccione como **Tipo de propiedad**.  
  
3.  Haga clic en **Finalizar**.  
  
4.  Declare una variable miembro de `CDataPathProperty`\- clase derivada a la clase de control ActiveX.  
  
     [!code-cpp[NVC_MFCActiveXControl#3](../mfc/codesnippet/CPP/activex-controls-on-the-internet_3.h)]  
  
5.  Implemente los métodos de **Get\/Set** .  Para **Get**, devuelva la cadena.  Para `Set`, cargue la propiedad y llama `SetModifiedFlag`.  
  
     [!code-cpp[NVC_MFCActiveXControl#4](../mfc/codesnippet/CPP/activex-controls-on-the-internet_4.cpp)]  
  
6.  En [DoPropExchange](../Topic/COleControl::DoPropExchange.md), agregue la línea siguiente:  
  
     [!code-cpp[NVC_MFCActiveXControl#5](../mfc/codesnippet/CPP/activex-controls-on-the-internet_5.cpp)]  
  
7.  Reemplazo [ResetData](../Topic/CDataPathProperty::ResetData.md) para notificar a la propiedad para restaurar su control agregando esta línea:  
  
     [!code-cpp[NVC_MFCActiveXControl#6](../mfc/codesnippet/CPP/activex-controls-on-the-internet_6.cpp)]  
  
## Si de decisión a Derive CDataPathProperty o de CCachedDataPathProperty  
 El ejemplo anterior se describen los pasos para derivar la propiedad del control de `CDataPathProperty`.  Esto es una buena opción si está descargando los datos en tiempo real que cambian con frecuencia, y para los que no necesita mantener todos los datos, pero solo el valor actual.  Un ejemplo es un control de cotización bursátil.  
  
 También puede derivar de `CCachedDataPathProperty`.  En este caso, los datos descargados se almacena en memoria caché en un archivo de memoria.  Esto es una buena opción si necesita conservar todos los datos descargados \(por ejemplo, un control que genere progresivamente un mapa de bits.  En este caso, la clase tiene una variable miembro que contiene los datos:  
  
 `CMemFile m_Cache;`  
  
 En la clase de control ActiveX, puede utilizar este archivo asignado memoria en `OnDraw` para mostrar los datos.  En el control ActiveX `CCachedDataPathProperty`\- clase derivada, reemplace la función `OnDataAvailable` miembro y reemplace el control, después de llamar a la implementación de la clase base.  
  
 [!code-cpp[NVC_MFCActiveXControl#7](../mfc/codesnippet/CPP/activex-controls-on-the-internet_7.cpp)]  
  
## Datos de forma asincrónica mediante Controles ActiveX  
 Los datos de transferencia sobre una red se deben realizar de forma asincrónica.  La ventaja de hacerlo es que si se transfiere una cantidad grande de datos o una conexión lenta, el proceso de descarga no bloqueará otros procesos del cliente.  
  
 Los monikeres asincrónicos proporcionan una forma de descargar datos de forma asincrónica sobre una red.  Una operación de lectura en un moniker asincrónico vuelve inmediatamente, incluso si la operación no ha finalizado.  
  
 Por ejemplo, si sólo 10 bytes están disponibles y la lectura se llama de forma asincrónica en un archivo 1K, lectura no bloquea, pero vuelve con los 10 bytes disponibles actualmente.  
  
 Implementa [monikeres asincrónicos](../mfc/asynchronous-monikers-on-the-internet.md) mediante la clase de `CAsyncMonikerFile` .  Sin embargo, los controles ActiveX pueden utilizar la clase de `CDataPathProperty` , que se deriva de `CAsyncMonikerFile`, para ayudar a implementar propiedades asincrónicas del control.  
  
 El ejemplo de ASYNDOWN muestra cómo configurar un bucle asincrónico mediante los temporizadores para leer los datos.  ASYNDOWN se describe en detalle en el artículo “HOWTO de Knowledge Base: Los datos asincrónicos de AsyncDown Muestra descargan” \(Q177244\) y están disponibles para su descarga desde el Centro de descarga de Microsoft. \(Para obtener más información sobre los archivos de la transferencia del Centro de descarga de Microsoft, vea el artículo “Cómo a los archivos de soporte técnico de Microsoft en Obtain de los servicios en línea” \(Q119591\) en Microsoft Knowledge Base\). Encontrará artículos de Knowledge Base en el CD\-ROM de MSDN Library o en [http:\/\/support.microsoft.com\/support\/](http://support.microsoft.com/support).  
  
 La técnica básica utilizada en ASYNDOWN es establecer un temporizador a **CDataPathProperty::OnDataAvailable** para indicar cuando los datos están disponibles.  Cuando se recibe el mensaje del temporizador, la aplicación lee 128 bloques de bytes de datos y rellena un control de edición.  Si los datos no está disponible cuando se procesa el mensaje del temporizador, se desactiva el temporizador.  `OnDataAvailable` gira el temporizador si resulta más datos más adelante.  
  
## Mostrar un Control en una página Web  
 A continuación se muestra un ejemplo de una etiqueta y los atributos del objeto para insertar un control en una página Web.  
  
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
  
## Actualizar un control OLE existente para utilizar características de controles ActiveX Nuevo  
 Si el control OLE se creó con una versión de Visual C\+\+ antes de 4,2, hay las medidas que puede tomar para mejorar su rendimiento y extender su funcionalidad.  Para obtener una explicación detallada de estos cambios, vea [Controles ActiveX: Optimización](../mfc/mfc-activex-controls-optimization.md).  
  
 Si está agregando compatibilidad asincrónico de propiedades a un control existente, necesitará agregar la propiedad de estado listo y el evento de `ReadyStateChange` personalmente.  En el constructor del control, agregue:  
  
 [!code-cpp[NVC_MFCActiveXControl#8](../mfc/codesnippet/CPP/activex-controls-on-the-internet_8.cpp)]  
  
 Actualizará el estado listo como el código es descargado llamando a [COleControl::InternalSetReadyState](../Topic/COleControl::InternalSetReadyState.md).  Uno se coloque podría llamar a `InternalSetReadyState` es de reemplazo de `CDataPathProperty`\- clase derivada de `OnProgress` .  
  
 A continuación, siga los pasos de [Crear un control ActiveX New](#_core_how_do_i_create_a_new_activex_control.3f).  
  
## Vea también  
 [Tareas de programación para Internet de MFC](../mfc/mfc-internet-programming-tasks.md)   
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)