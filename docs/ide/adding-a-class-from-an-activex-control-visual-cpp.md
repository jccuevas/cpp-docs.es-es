---
title: Agregar una clase desde un control ActiveX
ms.date: 11/08/2018
f1_keywords:
- vc.codewiz.class.axcontrol
helpviewer_keywords:
- ActiveX controls [C++], adding classes
- classes [C++], creating
- ActiveX Control Wizard
- add class from ActiveX control wizard [C++]
ms.assetid: 729fcb37-54b8-44d5-9b4e-50bb16e0eea4
ms.openlocfilehash: 1d91d98082a5c5d6d45bfa31e81c59e8925aa2c2
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694223"
---
# <a name="add-a-class-from-an-activex-control"></a>Agregar una clase desde un control ActiveX

Use este asistente para crear una clase MFC desde una interfaz en un control ActiveX disponible. Puede agregar una clase MFC a una [Aplicación MFC](../mfc/reference/creating-an-mfc-application.md), un archivo [DLL de MFC](../mfc/reference/creating-an-mfc-dll-project.md) o un [control ActiveX de MFC](../mfc/reference/creating-an-mfc-activex-control.md).

> [!WARNING]
> En Visual Studio 2017 versión 15.9, Microsoft ha dejado en desuso este asistente de código, que se quitará en una versión futura de Visual Studio. Este asistente se usa con muy poca frecuencia. La compatibilidad general con ATL y MFC no se ve afectada por la eliminación de este asistente. Si quiere compartir sus comentarios sobre este desuso, rellene [esta encuesta](https://www.surveymonkey.com/r/QDWKKCN). Su opinión es importante para nosotros.
<!-- Blank comment here to separate the warning and note. -->
> [!NOTE]
> No es necesario crear un proyecto MFC con Automation habilitado para agregar una clase desde un control ActiveX.

Un control ActiveX es un componente de software reutilizable basado en el Modelo de objetos componentes (COM) que admite una gran variedad de funciones OLE. Se puede personalizar para ajustarse a muchas necesidades del software. Puede usar controles ActiveX en contenedores de controles ActiveX estándar o en páginas web de Internet.

**Para agregar una clase MFC desde un control ActiveX:**

1. En el **Explorador de soluciones** o la [Vista de clases](/visualstudio/ide/viewing-the-structure-of-code), haga clic con el botón derecho en el nombre del proyecto al que quiera agregar la clase de control ActiveX.

1. En el menú contextual, elija **Agregar** y luego **Agregar clase**.

1. En el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), en el panel **Plantillas**, elija **Clase MFC de un control ActiveX** y luego **Abrir** para mostrar el [Asistente para agregar clases a partir de un control ActiveX](#add-class-from-activex-control-wizard).

En el asistente, se puede agregar más de una interfaz en un control ActiveX. También se pueden crear clases a partir de más de un control ActiveX en una única sesión del asistente.

Puede agregar clases desde controles ActiveX registrados en el sistema, o bien desde controles ActiveX situados en archivos de biblioteca de tipos (.tlb, .olb, .dll, .ocx o .exe) sin registrarlos primero en el sistema. Para obtener más información sobre el registro de controles ActiveX, vea [Registrar controles OLE](../mfc/reference/registering-ole-controls.md).

El asistente crea una clase MFC, derivada de [CWnd](../mfc/reference/cwnd-class.md) o de [COleDispatchDriver](../mfc/reference/coledispatchdriver-class.md), para cada interfaz que se agregue desde el control ActiveX seleccionado.

## <a name="in-this-section"></a>En esta sección

- [Asistente para agregar clases a partir de un control ActiveX](#add-class-from-activex-control-wizard)

## <a name="add-class-from-activex-control-wizard"></a>Asistente para agregar clases a partir de un control ActiveX

Use este asistente para agregar una clase MFC desde un control ActiveX disponible. El asistente crea una clase para cada interfaz que se agregue desde el control ActiveX seleccionado.

- **Agregar clase desde**

  Especifica la ubicación de la biblioteca de tipos desde la que se crea la clase.

  |Opción|Descripción|
  |------------|-----------------|
  |**Registry**|La biblioteca de tipos se registra en el sistema. Las bibliotecas de tipos registradas se enumeran en **Controles ActiveX disponibles**.|
  |**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema, pero se almacena en un archivo. Proporcione la ubicación del archivo en **Ubicación**.|

- **Controles ActiveX disponibles**

  Especifica los controles ActiveX registrados actualmente en el sistema. Seleccione un control ActiveX de esta lista para mostrar sus interfaces en la lista **Interfaces**. Vea [Controles ActiveX MFC: Distribuir controles ActiveX](../mfc/mfc-activex-controls-distributing-activex-controls.md) para obtener más información sobre el registro de controles ActiveX.

  Si selecciona **Archivo** en **Agregar clase desde**, este cuadro no se puede cambiar.

- **Ubicación**

  Especifica la ubicación del control ActiveX. Si selecciona **Archivo** en **Agregar clase desde**, puede proporcionar la ubicación del archivo que tiene la biblioteca de tipos. Para ir a la ubicación del archivo, seleccione el botón de puntos suspensivos.

  Si selecciona **Registro** en **Agregar clase desde**, este cuadro no se puede cambiar.

- **Interfaces**

  Especifica las interfaces del control ActiveX. El asistente usa las interfaces de la selección actual de **Controles ActiveX disponibles** o las interfaces del archivo de biblioteca de tipos especificado en **Ubicación**.

  |Botón de transferencia|Descripción|
  |---------------------|-----------------|
  |**>**|Agrega la interfaz seleccionada actualmente en la lista **Interfaces**. No está disponible si no se ha seleccionado ninguna interfaz.|
  |**>>**|Agrega todas las interfaces del control ActiveX. El asistente usa las interfaces de la selección actual de **Controles ActiveX disponibles** o las interfaces del archivo de biblioteca de tipos especificado en **Ubicación**.|
  |**\<**|Quita la clase seleccionada actualmente en la lista **Clases generadas**. No está disponible si no hay ninguna clase seleccionada actualmente en la lista **Clases generadas**.|
  |**\<\<**|Quita todas las clases de la lista **Clases generadas**. No está disponible si la lista **Clases generadas** está vacía.|

- **Clases generadas**

  Especifica los nombres de clase que se van a generar a partir de las interfaces agregadas con el botón **>** o **>>**. Puede activar esta casilla para seleccionar una clase y luego usar las teclas arriba o abajo para desplazarse por la lista. Al seleccionar **Finalizar**, puede ver cada nombre de clase generado en el cuadro **Clase** y cada nombre de archivo generado en el cuadro **Archivo .h**. Solo se puede seleccionar una clase a la vez en este cuadro.

  Puede quitar una clase si la selecciona en esta lista y luego selecciona **<**. No es necesario seleccionar una clase en el cuadro **Clases generadas** para quitar todas las clases. Al seleccionar **<<**, se quitan todas las clases del cuadro **Clases generadas**.

- **Clase**

   Especifica el nombre de la clase seleccionada en el cuadro **Clases generadas** que el asistente agrega al seleccionar **Finalizar**. Se puede modificar el nombre en el cuadro **Clase**.

- **Archivo .h**

  Establece el nombre del archivo de encabezado para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Clases generadas**. Seleccione el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que prefiera, o bien para anexar la declaración de clase a un archivo existente. Si elige un archivo existente, el asistente no lo guarda en la ubicación seleccionada hasta que se selecciona **Finalizar** en el asistente.

  El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente y luego **Finalizar**, el asistente le pide que indique si se debe anexar la declaración de clase al contenido del archivo. Seleccione **Sí** para anexar el archivo; seleccione **No** para volver al asistente y especificar otro nombre de archivo.

- **Archivo .cpp**

  Establece el nombre del archivo de implementación para la clase nueva del objeto. De forma predeterminada, este nombre se basa en el que se proporcione en **Clases generadas**. Seleccione el botón de puntos suspensivos para guardar el nombre de archivo en la ubicación que prefiera. El archivo no se guarda en la ubicación seleccionada hasta que se selecciona **Finalizar** en el asistente.

  El asistente no sobrescribe un archivo. Si selecciona el nombre de un archivo existente y luego **Finalizar**, el asistente le pide que indique si se debe anexar la implementación de clase al contenido del archivo. Seleccione **Sí** para anexar el archivo; seleccione **No** para volver al asistente y especificar otro nombre de archivo.
