---
title: Controles ActiveX MFC
ms.date: 11/19/2018
f1_keywords:
- MFC ActiveX Controls (MFC)
helpviewer_keywords:
- COleControl class [MFC], MFC ActiveX controls
- ActiveX controls [MFC], MFC
- containers [MFC], MFC ActiveX controls
- MFC ActiveX controls [MFC], serializing
- MFC ActiveX controls [MFC], containers
- serialization [MFC], MFC ActiveX controls
- dispatch maps [MFC], for MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- events [MFC], ActiveX controls
- MFC ActiveX controls [MFC]
ms.assetid: c911fb74-3afc-4bf3-a0f5-7922b14d9a1b
ms.openlocfilehash: a1c7bb070a75f4406556817163931f0707706c40
ms.sourcegitcommit: 389c559918d9bfaf303d262ee5430d787a662e92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "69508127"
---
# <a name="mfc-activex-controls"></a>Controles ActiveX MFC

Un control ActiveX es un componente de software reutilizable, basado en el modelo de objetos componentes (COM), que admite una gran variedad de funciones OLE y se puede personalizar de modo que se adapte a las necesidades del software.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información, vea [controles ActiveX](activex-controls.md).

Los controles ActiveX están diseñados para su uso tanto en contenedores de controles ActiveX ordinarios como en páginas web de Internet. Puede crear controles ActiveX con MFC, que se describen aquí, o con el [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).

Un control ActiveX puede dibujarse por sí mismo en su propia ventana, responde a eventos (por ejemplo, los clics del mouse) y se administra a través de una interfaz que incluye propiedades y métodos similares a los de los objetos de automatización.

Estos controles se pueden desarrollar para muchos usos, por ejemplo, acceso a bases de datos, supervisión de datos o representación gráfica. Además de su portabilidad, los controles ActiveX admiten ahora características que previamente no estaban disponibles, como compatibilidad con contenedores OLE existentes y la capacidad de integrar sus menús con los del contenedor OLE. Además, un control ActiveX admite totalmente la automatización, que permite al control exponer propiedades de lectura/escritura y un conjunto de métodos a los que puede llamar el usuario del control.

Puede crear controles ActiveX sin ventana y controles que solo crean una ventana cuando pasan a ser activos. Los controles sin ventana aceleran la presentación de la aplicación y permiten tener controles transparentes y no rectangulares. Las propiedades de los controles ActiveX también pueden cargarse de forma asincrónica.

Un control ActiveX se implementa como un servidor en proceso (normalmente un pequeño objeto) que se puede utilizar en cualquier contenedor OLE. Observe que la funcionalidad completa de un control ActiveX solo está disponible cuando se utiliza dentro de un contenedor OLE diseñado para tener en cuenta los controles ActiveX. Vea [portar controles ActiveX a otras aplicaciones](../mfc/containers-for-activex-controls.md) para obtener una lista de contenedores que admiten controles ActiveX. Este tipo de contenedor, en lo sucesivo denominado "contenedor de control", puede operar un control ActiveX mediante las propiedades y métodos del control, y recibe notificaciones del control ActiveX en forma de eventos. En la figura siguiente se muestra esta interacción.

![Interacción del control y el contenedor de controles ActiveX](../mfc/media/vc37221.gif "Interacción del control y el contenedor de controles ActiveX") <br/>
Interacción entre un contenedor de controles ActiveX y un control ActiveX con ventanas

Para obtener información reciente sobre cómo optimizar los controles ActiveX, vea [controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md).

Para crear un control ActiveX de MFC, vea [crear un proyecto de control ActiveX](../mfc/reference/mfc-activex-control-wizard.md).

Para obtener más información, consulte:

- [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

- [Documentos activos](../mfc/active-documents.md)

- [Descripción de los controles ActiveX](/windows/win32/com/activex-controls)

- [Actualizar un control ActiveX existente para usarlo en Internet](../mfc/upgrading-an-existing-activex-control.md)

##  <a name="_core_basic_components_of_an_activex_control"></a>Componentes básicos de un control ActiveX

Un control ActiveX utiliza varios elementos de programación para interactuar eficazmente con un contenedor de controles y con el usuario. Se trata de la clase [COleControl](../mfc/reference/colecontrol-class.md), un conjunto de funciones de activación de eventos y un mapa de envío.

Cada objeto de control ActiveX que se desarrolla hereda un conjunto eficaz de características de la clase base de MFC, `COleControl`. Estas características incluyen la activación en contexto y la lógica de automatización. `COleControl` puede proporcionar el objeto de control con la misma funcionalidad que un objeto de ventana de MFC, más la capacidad de desencadenar eventos. `COleControl`también puede proporcionar [controles sin ventana](../mfc/providing-windowless-activation.md), que dependen de su contenedor para obtener ayuda con algunas de las funciones que proporciona una ventana (captura del mouse, foco del teclado, desplazamiento), pero ofrece una presentación mucho más rápida.

Dado que la clase control se deriva de `COleControl`, hereda la capacidad de enviar, o "desencadena", los mensajes, denominados eventos, para el contenedor del control cuando se cumplen ciertas condiciones. Estos eventos se usan para notificar al contenedor del control cuando algo importante ocurre en el control. Puede enviar información adicional sobre un evento al contenedor del control si asocia parámetros al evento. Para obtener más información acerca de los eventos de control ActiveX [, vea el artículo controles ActiveX de MFC: Eventos](../mfc/mfc-activex-controls-events.md).

El último elemento es un mapa de envíos, que se utiliza para exponer un conjunto de funciones (denominadas métodos) y atributos (denominados propiedades) al usuario del control. Las propiedades permiten que el contenedor del control o el usuario del control lo manipulen de varias maneras. El usuario puede cambiar el aspecto del control, cambiar algunos valores del control o hacer solicitudes del control, por ejemplo, obtener acceso a una parte específica de los datos que el control mantiene. Esta interfaz viene determinada por el desarrollador del control y se define mediante **vista de clases**. Para obtener más información sobre los métodos y propiedades de controles ActiveX, [vea los artículos controles ActiveX de MFC: Métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md).

##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a>Interacción entre controles con Windows y contenedores de controles ActiveX

Cuando un control se utiliza dentro de un contenedor, utiliza dos mecanismos para la comunicación: expone propiedades y métodos, y desencadena eventos. En la ilustración siguiente se muestra cómo se implementan estos dos mecanismos.

![El control ActiveX se comunica con su contenedor](../mfc/media/vc37222.gif "El control ActiveX se comunica con su contenedor") <br/>
Comunicación entre un contendor de controles ActiveX y un control ActiveX

En la ilustración anterior se muestra también cómo los controles administran otras interfaces OLE (además de la automatización y los eventos).

`COleControl` realiza toda la comunicación de un control con el contenedor. Para controlar algunas de las solicitudes del contenedor, `COleControl` llamará a las funciones miembro que se implementan en la clase del control. Todos los métodos y algunas propiedades se controlan de esta manera. La clase del control también puede iniciar la comunicación con el contenedor si se llama a las funciones miembro de `COleControl`. Los eventos se desencadenan de esta manera.

##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a>Estados activos e inactivos de un control ActiveX

Un control tiene dos estados básicos: activo e inactivo. Tradicionalmente, se distinguían por el hecho de que el control tuviera o no una ventana. Un control activo tenía una ventana; un control inactivo no la tenía. Con la introducción de la activación sin ventana, esta distinción ya no es universal, pero sigue aplicándose a muchos controles.

Cuando un [control sin ventana](../mfc/providing-windowless-activation.md) se activa, invoca la captura del mouse, el foco de teclado, el desplazamiento y otros servicios de ventana desde su contenedor. También puede [proporcionar interacción con el mouse a controles inactivos](../mfc/providing-mouse-interaction-while-inactive.md), así como crear controles que [esperan hasta que se activen para crear una ventana](../mfc/turning-off-the-activate-when-visible-option.md).

Cuando un control con una ventana se activa, puede interactuar completamente con el contenedor, el usuario y Windows. En la ilustración siguiente se muestran las rutas de comunicación entre el control ActiveX, el contenedor y el sistema operativo.

![Procesamiento de mensajes en el control ActiveX con ventanas activas](../mfc/media/vc37223.gif "Procesamiento de mensajes en el control ActiveX con ventanas activas") <br/>
Procesamiento de mensajes de ventanas en un control ActiveX con ventanas (cuando esté activo)

##  <a name="_core_serializing_activex_elements"></a>Serialización

La capacidad de serializar los datos, a la que a veces se hace referencia como persistencia, permite que el control escriba el valor de las propiedades en el almacenamiento persistente. Los controles pueden volver a crearse entonces si se lee el estado del objeto en el almacenamiento.

Tenga en cuenta que un control no es responsable de obtener acceso al soporte de almacenamiento. En su lugar, el contenedor del control es responsable de proporcionar al control un medio de almacenamiento para usarlo en el momento adecuado. Para obtener más información sobre la serialización, vea [el artículo controles ActiveX de MFC: Serializando](../mfc/mfc-activex-controls-serializing.md). Para obtener información sobre cómo optimizar la serialización, vea [optimizar la persistencia y la inicialización](../mfc/optimizing-persistence-and-initialization.md) en controles ActiveX: Optimización.

##  <a name="_core_installing_activex_control_classes_and_tools"></a>Instalar herramientas y clases de controles ActiveX

Cuando se instala Visual C++, las clases de control ActiveX de MFC y las DLL en tiempo de ejecución de control ActiveX para la versión de lanzamiento y depuración se instalan automáticamente si los controles ActiveX están seleccionados en Configuración (lo están de forma predeterminada).

De forma predeterminada, las clases y herramientas de controles ActiveX se instalan en los siguientes subdirectorios en \Archivos de Programa\microsoft Visual Studio .NET:

- **\Common7\Tools**

   Contiene los archivos del contenedor de prueba (TstCon32.exe, así como los archivos de Ayuda).

- **\Vc7\atlmfc\include**

   Contiene los archivos de inclusión necesarios para desarrollar controles ActiveX con MFC

- **\Vc7\atlmfc\src\mfc**

   Contiene el código fuente de las clases de control ActiveX específicas de MFC

- **\Vc7\atlmfc\lib**

   Contiene las bibliotecas necesarias para desarrollar controles ActiveX con MFC

También hay ejemplos para controles ActiveX de MFC. Para obtener más información acerca de estos ejemplos [, vea ejemplos de controles: Controles ActiveX basados en MFC](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
