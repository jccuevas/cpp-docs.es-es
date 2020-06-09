---
title: Controles ActiveX en Internet
ms.date: 09/12/2018
helpviewer_keywords:
- ActiveX controls [MFC], creating
- ActiveX controls [MFC], Internet
- downloading data with ActiveX controls
- OLE controls [MFC], upgrading to ActiveX
- Internet applications [MFC], ActiveX controls
- networks [MFC], downloading with ActiveX controls
ms.assetid: 7ab943c8-2022-41df-9065-d629b616eeec
ms.openlocfilehash: f06a6f6f71e922163fd95c59836c50b88b05ed3a
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616476"
---
# <a name="activex-controls-on-the-internet"></a>Controles ActiveX en Internet

Los controles ActiveX son la versión actualizada de la especificación de controles OLE.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información, vea [controles ActiveX](activex-controls.md).

Los controles son una arquitectura principal para el desarrollo de componentes de software programables que se pueden usar en varios contenedores diferentes, incluidos los exploradores Web compatibles con COM en Internet. Cualquier control ActiveX puede ser un control de Internet y puede agregar su funcionalidad a un documento activo o formar parte de una página web. Los controles de una página web pueden comunicarse entre sí mediante scripting.

Los controles ActiveX no se limitan a Internet. Un control ActiveX también puede usarse en cualquier contenedor, siempre que el control admita las interfaces requeridas por ese contenedor.

**Los controles ActiveX tienen varias ventajas, entre las que se incluyen:**

- Menos interfaces necesarias que los controles OLE anteriores.

- La capacidad de tener ventanas y siempre activas.

**Para ser un control ActiveX, un control debe:**

- Compatibilidad con la `IUnknown` interfaz.

- Ser un objeto COM.

- Exportar **DllRegisterServer** y **DLLUnRegisterServer**.

- Admitir interfaces adicionales según sea necesario para la funcionalidad.

## <a name="making-your-existing-controls-internet-friendly"></a>Crear controles existentes para Internet

Para diseñar un control que funcione bien en un entorno de Internet, es necesario tener en cuenta las tarifas de transmisión relativamente bajas en Internet. Puede usar los controles existentes; sin embargo, hay pasos que debe seguir para reducir el tamaño del código y hacer que las propiedades de control se descarguen de forma asincrónica.

Para mejorar el rendimiento de los controles, siga estas sugerencias sobre consideraciones de eficacia:

- Implemente las técnicas descritas en el artículo [controles ActiveX: optimización](mfc-activex-controls-optimization.md).

- Tenga en cuenta cómo se crea una instancia de un control.

- Ser asincrónico; no conserve otros programas.

- Descargar datos en bloques pequeños.

   Cuando descargue grandes flujos, como mapas de bits o datos de vídeo, obtenga acceso a los datos de un control de forma asincrónica en cooperación con el contenedor. Recupere los datos de manera incremental o progresiva, trabajando de forma cooperativa con otros controles que también pueden estar recuperando datos. También se puede descargar el código de forma asincrónica.

- Descargue el código y las propiedades en segundo plano.

- Conviértase en la interfaz de usuario activa lo más rápido posible.

- Tenga en cuenta cómo se almacenan los datos persistentes, las propiedades y los blobs de datos de gran tamaño (por ejemplo, una imagen de mapa de bits o datos de vídeo).

   Los controles con grandes cantidades de datos persistentes, como mapas de bits de gran tamaño o archivos AVI, requieren especial atención al método de descarga. Un documento o una página pueden estar visibles lo antes posible y permitir que el usuario interactúe con la página mientras los controles recuperan datos en segundo plano.

- Escriba rutinas eficaces para mantener el tamaño del código y el tiempo de ejecución.

   Los controles de botón y etiqueta pequeños, con solo unos pocos bytes de datos persistentes, son adecuados para su uso en el entorno de Internet y funcionan bien dentro de los exploradores.

- Tenga en cuenta que el progreso se comunica con el contenedor.

   Notifique al contenedor de progreso en la descarga asincrónica, incluso cuando el usuario pueda empezar a interactuar con una página y cuando se haya completado la descarga. El contenedor puede mostrar el progreso (como el porcentaje completado) al usuario.

- Tenga en cuenta cómo se registran los controles en el equipo cliente.

## <a name="creating-a-new-activex-control"></a>Crear un nuevo control ActiveX

Al crear un nuevo control mediante el Asistente para aplicaciones, puede elegir habilitar la compatibilidad con los monikers asincrónicos, así como con otras optimizaciones. Para agregar compatibilidad para descargar las propiedades de control de forma asincrónica, siga estos pasos:

#### <a name="to-create-your-project-using-the-mfc-activex-control-wizard"></a>Para crear el proyecto mediante el Asistente para controles ActiveX MFC

1. En el menú **archivo** , haga clic en **nuevo** .

1. Seleccione **Asistente para controles ActiveX MFC** en los proyectos de Visual Studio C++ y asigne un nombre al proyecto.

1. En la página **configuración del control** , seleccione **cargar propiedades de forma asincrónica**. Al seleccionar esta opción, se establece la propiedad estado listo y el evento cambio de estado listo.

   También puede seleccionar otras optimizaciones, como la **activación sin ventanas**, que se describe en [controles ActiveX: optimización](mfc-activex-controls-optimization.md).

1. Haga clic en **Finalizar** para crear el proyecto.

#### <a name="to-create-a-class-derived-from-cdatapathproperty"></a>Para crear una clase derivada de CDataPathProperty

1. Cree una clase derivada de `CDataPathProperty` .

1. En cada uno de los archivos de código fuente que incluye el archivo de encabezado del control, agregue el archivo de encabezado para esta clase antes.

1. En esta clase, invalide `OnDataAvailable` . Se llama a esta función cada vez que los datos están disponibles para su presentación. A medida que los datos estén disponibles, puede controlarlos de la forma que elija, por ejemplo, al representarlos progresivamente.

   El fragmento de código siguiente es un ejemplo sencillo de la visualización progresiva de datos en un control de edición. Observe el uso de la marca **BSCF_FIRSTDATANOTIFICATION** para borrar el control de edición.

   [!code-cpp[NVC_MFCActiveXControl#1](codesnippet/cpp/activex-controls-on-the-internet_1.cpp)]

   Tenga en cuenta que debe incluir AFXCMN. H para utilizar la `CListCtrl` clase.

1. Cuando cambie el estado general del control (por ejemplo, de carga a inicializado o de usuario interactivo), llame a `COleControl::InternalSetReadyState` . Si el control solo tiene una propiedad de ruta de acceso de datos, puede agregar código en **BSCF_LASTDATANOTIFICATION** para notificar al contenedor que la descarga se ha completado. Por ejemplo:

   [!code-cpp[NVC_MFCActiveXControl#2](codesnippet/cpp/activex-controls-on-the-internet_2.cpp)]

1. Reemplace `OnProgress`. En `OnProgress` , se pasa un número que muestra el intervalo máximo y un número que indica la distancia de la descarga actual. Puede usar estos números para mostrar el estado como porcentaje completado al usuario.

En el procedimiento siguiente se agrega una propiedad al control para utilizar la clase simplemente derivada.

#### <a name="to-add-a-property"></a>Para agregar una propiedad

1. En **vista de clases**, haga clic con el botón secundario en la interfaz debajo del nodo biblioteca y seleccione **Agregar**y, a continuación, **Agregar propiedad**. Se iniciará el **Asistente para agregar propiedades**.

1. En el **Asistente para agregar propiedades**, seleccione el botón de radio **establecer/obtener métodos** , escriba el nombre de la **propiedad**, por ejemplo, EditControlText, y seleccione BSTR como el **tipo de propiedad**.

1. Haga clic en **Finalizar**

1. Declare una variable miembro de la `CDataPathProperty` clase derivada de en la clase de control ActiveX.

   [!code-cpp[NVC_MFCActiveXControl#3](codesnippet/cpp/activex-controls-on-the-internet_3.h)]

1. Implemente los métodos `Get/Set`. Para `Get` , devuelve la cadena. Para `Set` , cargue la propiedad y llame a `SetModifiedFlag` .

   [!code-cpp[NVC_MFCActiveXControl#4](codesnippet/cpp/activex-controls-on-the-internet_4.cpp)]

1. En [DoPropExchange](reference/colecontrol-class.md#dopropexchange), agregue la siguiente línea:

   [!code-cpp[NVC_MFCActiveXControl#5](codesnippet/cpp/activex-controls-on-the-internet_5.cpp)]

1. Invalide [ResetData](reference/cdatapathproperty-class.md#resetdata) para notificar a la propiedad que restablezca su control agregando esta línea:

   [!code-cpp[NVC_MFCActiveXControl#6](codesnippet/cpp/activex-controls-on-the-internet_6.cpp)]

## <a name="deciding-whether-to-derive-from-cdatapathproperty-or-ccacheddatapathproperty"></a>Decidir si derivar de CDataPathProperty o CCachedDataPathProperty

En el ejemplo anterior se describen los pasos para derivar la propiedad del control de `CDataPathProperty` . Esta es una buena opción si va a descargar datos en tiempo real que cambian con frecuencia y para los que no necesita conservar todos los datos, sino solo el valor actual. Un ejemplo es un control de tablero de cotizaciones.

También puede derivar de `CCachedDataPathProperty` . En este caso, los datos descargados se almacenan en caché en un archivo de memoria. Esta es una buena opción si necesita conservar todos los datos descargados, por ejemplo, un control que represente progresivamente un mapa de bits. En este caso, la clase tiene una variable miembro que contiene los datos:

`CMemFile m_Cache;`

En la clase de control ActiveX, puede utilizar este archivo asignado `OnDraw` a la memoria en para mostrar los datos. En la `CCachedDataPathProperty` clase derivada de control ActiveX, invalide la función miembro `OnDataAvailable` e invalide el control después de llamar a la implementación de la clase base.

[!code-cpp[NVC_MFCActiveXControl#7](codesnippet/cpp/activex-controls-on-the-internet_7.cpp)]

## <a name="downloading-data-asynchronously-using-activex-controls"></a>Descargar datos de forma asincrónica mediante controles ActiveX

La descarga de datos a través de una red debe realizarse de forma asincrónica. La ventaja de hacerlo es que si se transfiere una gran cantidad de datos o si la conexión es lenta, el proceso de descarga no bloqueará otros procesos en el cliente.

Los monikers asincrónicos proporcionan una manera de descargar datos de forma asincrónica a través de una red. Una operación de lectura en un moniker asincrónico se devuelve inmediatamente, aunque no se haya completado la operación.

Por ejemplo, si solo hay 10 bytes disponibles y se llama a Read de forma asincrónica en un archivo de 1K, Read no se bloquea, pero devuelve con los 10 bytes disponibles actualmente.

Los [monikers asincrónicos](asynchronous-monikers-on-the-internet.md) se implementan mediante la `CAsyncMonikerFile` clase. Sin embargo, los controles ActiveX pueden utilizar la `CDataPathProperty` clase, que se deriva de `CAsyncMonikerFile` , para ayudar a implementar propiedades de control asincrónicas.

## <a name="displaying-a-control-on-a-web-page"></a>Mostrar un control en una página web

A continuación se muestra un ejemplo de una etiqueta de objeto y atributos para insertar un control en una página web.

```xml
<OBJECT
  CLASSID="clsid:FC25B780-75BE-11CF-8B01-444553540000"
  CODEBASE="/ie/download/activex/iechart.ocx"
  ID=chart1
  WIDTH=400
  HEIGHT=200
  ALIGN=center
  HSPACE=0
  VSPACE=0>
  <PARAM NAME="BackColor" value="#ffffff"/>
  <PARAM NAME="ForeColor" value="#0000ff"/>
  <PARAM NAME="url" VALUE="/ie/controls/chart/mychart.txt"/>
</OBJECT>
```

## <a name="updating-an-existing-ole-control-to-use-new-activex-control-features"></a>Actualizar un control OLE existente para usar las nuevas características de controles ActiveX

Si el control OLE se creó con una versión de Visual C++ anterior a la 4,2, hay pasos que puede seguir para mejorar su rendimiento y mejorar su funcionalidad. Para obtener una explicación detallada de estos cambios, vea [controles ActiveX: optimización](mfc-activex-controls-optimization.md).

Si va a agregar compatibilidad con propiedades asincrónicas a un control existente, tendrá que agregar la propiedad estado listo y el `ReadyStateChange` evento usted mismo. En el constructor del control, agregue:

[!code-cpp[NVC_MFCActiveXControl#8](codesnippet/cpp/activex-controls-on-the-internet_8.cpp)]

Actualizará el estado listo a medida que se descarga el código mediante una llamada a [COleControl:: InternalSetReadyState](reference/colecontrol-class.md#internalsetreadystate). Una de las ubicaciones a las que se podía llamar `InternalSetReadyState` es desde la `OnProgress` invalidación de la `CDataPathProperty` clase derivada de.

## <a name="see-also"></a>Consulte también

[Tareas de programación para Internet de MFC](mfc-internet-programming-tasks.md)<br/>
[Fundamentos de la programación para Internet de MFC](mfc-internet-programming-basics.md)
