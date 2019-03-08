---
title: Implementar una interfaz
ms.date: 11/12/2018
f1_keywords:
- vc.codewiz.impl.interface.overview
helpviewer_keywords:
- interfaces, implementing
- implement interface wizard [C++]
ms.assetid: 72f8731b-7e36-45db-8b10-7ef211a773cd
ms.openlocfilehash: 8e166f806d247cd93ff0f471360d749fa95e430b
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51692906"
---
# <a name="implement-an-interface"></a>Implementar una interfaz

Para implementar una interfaz, debe haber creado un proyecto como una aplicación COM de ATL o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a la aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de ATL con una aplicación MFC.

Una vez creado el proyecto, para implementar una interfaz, primero debe agregar un objeto ATL. Vea [Agregar objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos al proyecto ATL.

> [!NOTE]
> El asistente no admite cuadros de diálogo de ATL, servicios web XML que usan ATL, objetos de rendimiento ni contadores de rendimiento.

Si [agrega un control ATL](../atl/reference/adding-an-atl-control.md), puede especificar si se van a implementar interfaces predeterminadas. Las interfaces predeterminadas se muestran en la página [Interfaces](../atl/reference/interfaces-atl-control-wizard.md) de ese asistente y se definen en atlcom.h.

Después de agregar el objeto o control, puede implementar otras interfaces que se encuentren en cualquier biblioteca de tipos disponible mediante el Asistente para implementar interfaces.

Si va a incorporar una interfaz nueva, debe agregarla de forma manual al archivo .idl del proyecto. Para obtener más información, vea [Agregar una nueva interfaz a un proyecto ATL](../atl/reference/adding-a-new-interface-in-an-atl-project.md).

**Para implementar una interfaz:**

1. En la Vista de clases, haga clic con el botón derecho en el nombre de clase para el objeto ATL.

1. Elija **Agregar** en el menú contextual y luego **Implementar interfaz** para mostrar el [Asistente para implementar interfaces](#implement-interface-wizard).

1. Seleccione las interfaces que se van a implementar desde las bibliotecas de tipos adecuadas y luego **Finalizar**.

1. En la Vista de clases, expanda el nodo Bases e interfaces del objeto para ver la interfaz que ha implementado. Luego expanda el nodo de la interfaz para ver sus propiedades, métodos y eventos disponibles.

   > [!NOTE]
   > También puede usar el [Examinador de objetos](/visualstudio/ide/viewing-the-structure-of-code) para examinar los miembros de la interfaz.

## <a name="in-this-section"></a>En esta sección

- [Asistente para implementar interfaces](#implement-interface-wizard)

## <a name="implement-interface-wizard"></a>Asistente para implementar interfaces

Este asistente implementa una interfaz para un objeto COM. Las implementaciones de muchas interfaces se incluyen en las bibliotecas COM disponibles con Visual Studio y Windows. Se asocia una implementación de interfaz a un objeto cuando se crea una instancia de ese objeto. Además, proporciona los servicios que ofrece el objeto.

Para obtener una explicación de las interfaces y las implementaciones, vea [Interfaces and interface implementations](/windows/desktop/com/interfaces-and-interface-implementations) (Interfaces e implementaciones de interfaz) en Windows SDK.

- **Implementar interfaz desde**

  Especifica la ubicación de la biblioteca de tipos, desde la que se crea la interfaz.

  |Opción|Descripción|
  |------------|-----------------|
  |**Proyecto**|La biblioteca de tipos forma parte del proyecto.|
  |**Registry**|La biblioteca de tipos se registra en el sistema. Las bibliotecas de tipos registradas se enumeran en **Bibliotecas de tipos disponibles**.|
  |**Archivo**|La biblioteca de tipos no está necesariamente registrada en el sistema, pero se conserva en un archivo. Proporcione la ubicación del archivo en **Ubicación**.|

- **Bibliotecas de tipos disponibles**

  Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz que se pueden implementar. Si elige **Archivo** en **Implementar interfaz desde**, este cuadro no se puede cambiar.

- **Ubicación**

  Muestra la ubicación de la biblioteca de tipos seleccionada actualmente en la lista **Bibliotecas de tipos disponibles**. Si ha seleccionado **Archivo** en **Implementar interfaz desde**, seleccione el botón de puntos suspensivos para buscar un archivo que contenga la biblioteca de tipos que se va a usar.

- **Interfaces**

  Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos seleccionada actualmente en el cuadro **Bibliotecas de tipos disponibles**.

  > [!NOTE]
  > Las interfaces con el mismo nombre que las ya implementadas por el objeto seleccionado no se muestran en el cuadro **Interfaces**.

  |Botón de transferencia|Descripción|
  |---------------------|-----------------|
  |**>**|Agrega el nombre de interfaz seleccionado actualmente en la lista **Interfaces** a la lista **Implementar interfaces**.|
  |**>>**|Agrega todos los nombre de interfaz disponibles en la lista **Interfaces** a la lista **Implementar interfaces**.|
  |**\<**|Quita el nombre de interfaz seleccionado actualmente en la lista **Implementar interfaces**.|
  |**\<\<**|Quita todos los nombres de interfaz que se muestran actualmente en la lista **Implementar interfaces**.|

- **Implementar Interfaces**

  Muestra los nombres de las interfaces que ha seleccionado para implementar en el objeto.

  > [!NOTE]
  > Si incluye más de una interfaz que se derive de `IDispatch`, o si intenta implementar una interfaz que se derive de otra ya presente en la clase, tiene que eliminar la ambigüedad de las entradas COM_MAP. Para obtener más información, vea [COM_INTERFACE_ENTRY2](../atl/reference/com-interface-entry-macros.md#com_interface_entry2).
