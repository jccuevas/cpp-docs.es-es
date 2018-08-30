---
title: Controles ActiveX de MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- MFC ActiveX Controls (MFC)
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9f0f0d88274e6804d087f8acf905ba3181d57798
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43205847"
---
# <a name="mfc-activex-controls"></a>Controles ActiveX MFC
Un control ActiveX es un componente de software reutilizable, basado en el modelo de objetos componentes (COM), que admite una gran variedad de funciones OLE y se puede personalizar de modo que se adapte a las necesidades del software. Los controles ActiveX están diseñados para su uso tanto en contenedores de controles ActiveX ordinarios como en páginas web de Internet. Puede crear controles ActiveX con MFC, descrita aquí, o con el [Active Template Library (ATL)](../atl/active-template-library-atl-concepts.md).  
  
 Un control ActiveX puede dibujarse por sí mismo en su propia ventana, responde a eventos (por ejemplo, los clics del mouse) y se administra a través de una interfaz que incluye propiedades y métodos similares a los de los objetos de Automation.  
  
 Estos controles se pueden desarrollar para muchos usos, por ejemplo, acceso a bases de datos, supervisión de datos o representación gráfica. Además de su portabilidad, los controles ActiveX admiten ahora características que previamente no estaban disponibles, como compatibilidad con contenedores OLE existentes y la capacidad de integrar sus menús con los del contenedor OLE. Además, un control ActiveX admite totalmente la automatización, que permite al control exponer propiedades de lectura/escritura y un conjunto de métodos a los que puede llamar el usuario del control.  
  
 Puede crear controles ActiveX sin ventana y controles que solo crean una ventana cuando pasan a ser activos. Los controles sin ventana aceleran la presentación de la aplicación y permiten tener controles transparentes y no rectangulares. Las propiedades de los controles ActiveX también pueden cargarse de forma asincrónica.  
  
 Un control ActiveX se implementa como un servidor en proceso (normalmente un pequeño objeto) que se puede utilizar en cualquier contenedor OLE. Observe que la funcionalidad completa de un control ActiveX solo está disponible cuando se utiliza dentro de un contenedor OLE diseñado para tener en cuenta los controles ActiveX. Consulte [portar controles ActiveX a otras aplicaciones](../mfc/containers-for-activex-controls.md) para obtener una lista de contenedores que admiten controles ActiveX. Este tipo de contenedor, en lo sucesivo denominado "contenedor de control", puede operar un control ActiveX mediante las propiedades y métodos del control, y recibe notificaciones del control ActiveX en forma de eventos. En la figura siguiente se muestra esta interacción.  
  
 ![Interacción de contenedor de controles ActiveX y control](../mfc/media/vc37221.gif "vc37221")  
Interacción entre un contenedor de controles ActiveX y un control ActiveX con ventanas  
  
 Para información reciente sobre la optimización de controles ActiveX, vea [controles ActiveX MFC: optimización](../mfc/mfc-activex-controls-optimization.md).  
  
 Para crear un control ActiveX de MFC, vea [crear un proyecto de control ActiveX](../mfc/reference/mfc-activex-control-wizard.md).  
  
 Para obtener más información, consulte:  
  
-   [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)  
  
-   [Documentos activos](../mfc/active-documents.md)  
  
-   [Descripción de los controles ActiveX](/windows/desktop/com/activex-controls)  
  
-   [Actualizar un ActiveX Control existente que se usará en Internet](../mfc/upgrading-an-existing-activex-control.md)  
  
##  <a name="_core_basic_components_of_an_activex_control"></a> Componentes básicos de un Control ActiveX  
 Un control ActiveX utiliza varios elementos de programación para interactuar eficazmente con un contenedor de controles y con el usuario. Estos son la clase [COleControl](../mfc/reference/colecontrol-class.md), un conjunto de funciones de activación de eventos y un envío mapa.  
  
 Cada objeto de control ActiveX que se desarrolla hereda un conjunto eficaz de características de la clase base de MFC, `COleControl`. Estas características incluyen la activación en contexto y la lógica de automatización. `COleControl` puede proporcionar el objeto de control con la misma funcionalidad que un objeto de ventana de MFC, más la capacidad de desencadenar eventos. `COleControl` También puede proporcionar [controles sin ventana](../mfc/providing-windowless-activation.md), que basan en su contenedor para obtener ayuda con la parte de la funcionalidad de una ventana proporciona (captura del mouse, foco de teclado, desplazamiento), pero ofrecen una presentación mucho más rápida.  
  
 Dado que la clase control se deriva de `COleControl`, hereda la capacidad de enviar, o "desencadena", los mensajes, denominados eventos, para el contenedor del control cuando se cumplen ciertas condiciones. Estos eventos se usan para notificar al contenedor del control cuando algo importante ocurre en el control. Puede enviar información adicional sobre un evento al contenedor del control si asocia parámetros al evento. Para obtener más información acerca de los eventos de control ActiveX, vea el artículo [controles ActiveX MFC: eventos](../mfc/mfc-activex-controls-events.md).  
  
 El último elemento es un mapa de envíos, que se utiliza para exponer un conjunto de funciones (denominadas métodos) y atributos (denominados propiedades) al usuario del control. Las propiedades permiten que el contenedor del control o el usuario del control lo manipulen de varias maneras. El usuario puede cambiar el aspecto del control, cambiar algunos valores del control o hacer solicitudes del control, por ejemplo, obtener acceso a una parte específica de los datos que el control mantiene. Esta interfaz viene determinada por el desarrollador del control y se define mediante **vista de clases**. Para obtener más información sobre las propiedades y métodos del control ActiveX, vea los artículos [controles ActiveX MFC: métodos](../mfc/mfc-activex-controls-methods.md) y [propiedades](../mfc/mfc-activex-controls-properties.md).  
  
##  <a name="_core_interaction_between_controls_with_windows_and_activex_control_containers"></a> Interacción entre los controles de Windows y los contenedores de controles ActiveX  
 Cuando un control se utiliza dentro de un contenedor, utiliza dos mecanismos para la comunicación: expone propiedades y métodos, y desencadena eventos. En la ilustración siguiente se muestra cómo se implementan estos dos mecanismos.  
  
 ![Control ActiveX se comunica con su contenedor](../mfc/media/vc37222.gif "vc37222")  
Comunicación entre un contendor de controles ActiveX y un control ActiveX  
  
 En la ilustración anterior se muestra también cómo los controles administran otras interfaces OLE (además de la automatización y los eventos).  
  
 `COleControl` realiza toda la comunicación de un control con el contenedor. Para controlar algunas de las solicitudes de contenedor, `COleControl` llamará a las funciones que se implementan en la clase de control de miembro. Todos los métodos y algunas propiedades se controlan de esta manera. La clase del control también puede iniciar la comunicación con el contenedor si se llama a las funciones miembro de `COleControl`. Los eventos se desencadenan de esta manera.  
  
##  <a name="_core_active_and_inactive_states_of_an_activex_control"></a> Estados activos e inactivos de un Control ActiveX  
 Un control tiene dos estados básicos: activo e inactivo. Tradicionalmente, se distinguían por el hecho de que el control tuviera o no una ventana. Un control activo tenía una ventana; un control inactivo no la tenía. Con la introducción de la activación sin ventana, esta distinción ya no es universal, pero sigue aplicándose a muchos controles.  
  
 Cuando un [control sin ventanas](../mfc/providing-windowless-activation.md) se activa, invoca la captura del mouse, foco de teclado, desplazamiento y otros servicios de la ventana de su contenedor. También puede [proporcionar interacción con el mouse a los controles inactivos](../mfc/providing-mouse-interaction-while-inactive.md), así como crear controles que [espere hasta que se activa para crear una ventana](../mfc/turning-off-the-activate-when-visible-option.md).  
  
 Cuando un control con una ventana se activa, puede interactuar completamente con el contenedor, el usuario y Windows. En la ilustración siguiente se muestran las rutas de comunicación entre el control ActiveX, el contenedor y el sistema operativo.  
  
 ![Procesamiento de mensajes en el control ActiveX con ventanas activo](../mfc/media/vc37223.gif "vc37223")  
Procesamiento de mensajes de ventanas en un control ActiveX con ventanas (cuando esté activo)  
  
##  <a name="_core_serializing_activex_elements"></a> Serialización  
 La capacidad de serializar los datos, a la que a veces se hace referencia como persistencia, permite que el control escriba el valor de las propiedades en el almacenamiento persistente. Los controles pueden volver a crearse entonces si se lee el estado del objeto en el almacenamiento.  
  
 Tenga en cuenta que un control no es responsable de obtener acceso al soporte de almacenamiento. En su lugar, el contenedor del control es responsable de proporcionar al control un medio de almacenamiento para usarlo en el momento adecuado. Para obtener más información sobre la serialización, vea el artículo [controles ActiveX MFC: serializar](../mfc/mfc-activex-controls-serializing.md). Para obtener información sobre cómo optimizar la serialización, vea [optimizar la persistencia y la inicialización](../mfc/optimizing-persistence-and-initialization.md) en los controles ActiveX: optimización.  
  
##  <a name="_core_installing_activex_control_classes_and_tools"></a> Instalar herramientas y clases de controles ActiveX  
 Cuando se instala Visual C++, las clases de control ActiveX de MFC y las DLL en tiempo de ejecución de control ActiveX para la versión de lanzamiento y depuración se instalan automáticamente si los controles ActiveX están seleccionados en Configuración (lo están de forma predeterminada).  
  
 De forma predeterminada, las clases de controles ActiveX y herramientas se instalan en los siguientes subdirectorios en \Program Files\Microsoft Visual Studio. NET:  
  
-   **\Common7\Tools**  
  
     Contiene los archivos del contenedor de prueba (TstCon32.exe, así como los archivos de Ayuda).  
  
-   **\Vc7\atlmfc\include**  
  
     Contiene los archivos de inclusión necesarios para desarrollar controles ActiveX con MFC  
  
-   **\Vc7\atlmfc\src\mfc**  
  
     Contiene el código fuente de las clases de control ActiveX específicas de MFC  
  
-   **\Vc7\atlmfc\lib**  
  
     Contiene las bibliotecas necesarias para desarrollar controles ActiveX con MFC  
  
 También hay ejemplos para controles ActiveX de MFC. Para obtener más información acerca de estos ejemplos, vea [ejemplos de controles: controles ActiveX](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Vea también  
 [Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)
