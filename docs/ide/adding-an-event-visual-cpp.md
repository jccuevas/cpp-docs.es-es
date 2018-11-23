---
title: Agregar un evento
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.event.overview
helpviewer_keywords:
- ActiveX controls [C++], adding events to
- MFC ActiveX controls [C++], adding events
- events [C++], ActiveX controls
- add event wizard [C++]
ms.assetid: fe34832a-edfc-4f86-aacb-8df77001873d
ms.openlocfilehash: 1d5a8f5666dd04e00f8a438fdbf00320c37e14f4
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693430"
---
# <a name="add-an-event"></a>Agregar un evento

Desde la Vista de clases, puede agregar un evento mediante el [Asistente para agregar eventos](#add-event-wizard) únicamente a la clase de control del proyecto [Control ActiveX MFC](../mfc/reference/creating-an-mfc-activex-control.md). Si quiere agregar un evento a otro tipo de proyecto, use el botón **Eventos** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

**Para agregar un evento al proyecto de control ActiveX MFC:**

1. En la Vista de clases, expanda el nodo del proyecto para mostrar las clases del proyecto.

1. Haga clic con el botón derecho en la clase de control del proyecto.

1. En el menú contextual, elija **Agregar** y luego **Agregar evento** para mostrar el Asistente para agregar eventos.

1. Proporcione la información del evento en los cuadros apropiados del asistente.

1. Seleccione **Finalizar** para agregar el evento al proyecto.

## <a name="in-this-section"></a>En esta sección

- [Asistente para agregar eventos](#add-event-wizard)

## <a name="add-event-wizard"></a>Asistente para agregar eventos

Este asistente agrega un evento a un proyecto de control ActiveX de MFC. Puede especificar un evento propio, personalizar un evento estándar típico o seleccionar en una lista de eventos estándar.

- **Nombre del evento**

   Establece el nombre que usan los clientes de Automation para solicitar un evento de la clase. Escriba un nombre o seleccione uno en la lista.

- **Tipo de evento**

   Indica el tipo de evento que se va a agregar. Solo está disponible si se selecciona en la lista **Nombre de evento**.

   |Opción|Descripción|
   |------------|-----------------|
   |**Estándar**|Especifica que un evento estándar, como un clic de botón, se implementará para esta clase. Los eventos estándar se definen en la biblioteca Microsoft Foundation Class (MFC).|
   |**Custom**|Especifica que se va a usar una implementación propia del evento.|

- **Nombre interno**

   Establece el nombre de la función miembro que envía el evento. Solo está disponible para los eventos personalizados. El nombre se basa en **Nombre del evento**. Se puede cambiar el nombre interno si se quiere proporcionar un nombre distinto al **Nombre del evento**.

- **Tipo de parámetro**

   Establece el tipo para el **Nombre de parámetro**. Seleccione el tipo de la lista.

- **Nombre del parámetro**

   Establece el nombre de un parámetro que se va a pasar a través del evento. Después de escribir el nombre, se debe seleccionar **Agregar** para agregarlo a la lista de parámetros.

   Después de seleccionar **Agregar**, el nombre del parámetro aparece en **Lista de parámetros**.

   > [!NOTE]
   > Si proporciona un nombre de parámetro y selecciona **Finalizar** antes de seleccionar **Agregar**, el parámetro no se agrega al evento. Debe buscar el método e insertar el parámetro de forma manual.

- **Add**

   Agrega el parámetro especificado en **Nombre del parámetro**, y su tipo, a la **Lista de parámetros**. Seleccione **Agregar** para agregar un parámetro a la lista.

- **Remove**

   Quita de la lista el parámetro seleccionado en **Lista de parámetros**.

- **Lista de parámetros**

   Muestra todos los parámetros y sus tipos agregados actualmente al método. A medida que se agregan los parámetros, el asistente actualiza **Lista de parámetros** para mostrar cada uno con su tipo.
