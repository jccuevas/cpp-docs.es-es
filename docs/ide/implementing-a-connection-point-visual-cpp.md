---
title: Implementar un punto de conexión
ms.date: 05/14/2019
helpviewer_keywords:
- connection points [C++], implementing
- implement connection point wizard [C++]
ms.assetid: 5b37e4f9-73c9-4bef-b26d-365bc0662260
ms.openlocfilehash: 8a75a5fbbabd20f4591e3a119c175d68cdfb1f90
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "66182605"
---
# <a name="implement-a-connection-point"></a>Implementar un punto de conexión

Para implementar un punto de conexión mediante el Asistente para implementar puntos de conexión, debe haber creado un proyecto como una aplicación COM de ATL o como una aplicación MFC que sea compatible con ATL. Puede usar el [Asistente para proyectos ATL](../atl/reference/atl-project-wizard.md) para crear una aplicación ATL, o bien [agregar un objeto ATL a la aplicación MFC](../mfc/reference/adding-atl-support-to-your-mfc-project.md) para implementar la compatibilidad de ATL con una aplicación MFC.

> [!NOTE]
> Para obtener información sobre cómo implementar puntos de conexión para un proyecto MFC, vea [Puntos de conexión](../mfc/connection-points.md).

Una vez creado el proyecto, para implementar un punto de conexión, primero debe agregar un objeto ATL. Vea [Adición de objetos y controles a un proyecto ATL](../atl/reference/adding-objects-and-controls-to-an-atl-project.md) para obtener una lista de los asistentes que agregan objetos al proyecto ATL.

> [!NOTE]
> El asistente no admite cuadros de diálogo de ATL, servicios web XML creados con servidor ATL, objetos de rendimiento ni contadores de rendimiento.

Un objeto conectable (es decir, un origen) puede mostrar un punto de conexión para cada una de sus interfaces de salida. Cada interfaz de salida se puede implementar mediante un cliente en un objeto (es decir, un receptor). Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).

**Para implementar un punto de conexión:**

1. En la Vista de clases, haga clic con el botón derecho en el nombre de clase para el objeto ATL.

1. Elija **Agregar** en el menú contextual y luego **Agregar punto de conexión** para mostrar el [Asistente para implementar puntos de conexión](#implement-connection-point-wizard).

1. Seleccione las interfaces de punto de conexión que se van a implementar desde las bibliotecas de tipos adecuadas y luego **Finalizar**.

1. En la Vista de clases, examine las clases de proxy creadas para cada punto de conexión. Las clases aparecen como CProxy*NombreDeInterfaz*\<T> y se derivan de [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md).

1. Haga doble clic en la clase de punto de conexión para mostrar la definición de clase del punto de conexión.

   - Si implementa un punto de conexión para la interfaz de un proyecto propio, aparece la definición siguiente:

     ```cpp
     template< class T >
     class CProxyInterfaceName :
     public IConnectionPointImpl< T, &IID_InterfaceName >
     {
     public:
     };
     ```

   - Si implementa una interfaz local, en el cuerpo de la clase aparecerán métodos y propiedades.

   - Si implementa un punto de conexión para otra interfaz, la definición incluye los métodos de la interfaz, precedidos de `Fire_`.

## <a name="in-this-section"></a>En esta sección

- [Asistente para implementar puntos de conexión](#implement-connection-point-wizard)

## <a name="implement-connection-point-wizard"></a>Asistente para implementar puntos de conexión

Este asistente implementa un punto de conexión para un objeto COM. Un objeto conectable (es decir, un origen) puede mostrar un punto de conexión para sus propias interfaces o para cualquier interfaz de salida. En MSVC y Windows se proporcionan bibliotecas de tipos que tienen interfaces de salida. Cada interfaz de salida se puede implementar mediante un cliente en un objeto (es decir, un receptor).

Para obtener más información, vea [Puntos de conexión en ATL](../atl/atl-connection-points.md).

- **Bibliotecas de tipos disponibles**

  Muestra las bibliotecas de tipos disponibles que contienen las definiciones de interfaz para las que se pueden implementar puntos de conexión. Seleccione el botón de puntos suspensivos para buscar un archivo que contenga la biblioteca de tipos que se va a usar.

- **Ubicación**

  Muestra la ubicación de la biblioteca de tipos seleccionada actualmente en la lista **Bibliotecas de tipos disponibles**.

- **Interfaces**

  Muestra las interfaces cuyas definiciones se encuentran en la biblioteca de tipos seleccionada actualmente en el cuadro **Bibliotecas de tipos disponibles**.

  |Botón de transferencia|Descripción|
  |---------------------|-----------------|
  |**>**|Agrega el nombre de interfaz seleccionado actualmente en la lista **Interfaces** a la lista **Implementar puntos de conexión**.|
  |**>>**|Agrega todos los nombres de interfaz disponibles en la lista **Interfaces** a la lista **Implementar puntos de conexión**.|
  |**\<**|Quita el nombre de interfaz seleccionado actualmente en la lista **Implementar puntos de conexión**.|
  |**\<\<**|Quita todos los nombres de interfaz que se muestran actualmente en la lista **Implementar puntos de conexión**.|

- **Implementar puntos de conexión**

  Muestra los nombres de las interfaces para las que se implementan los puntos de conexión al seleccionar **Finalizar**.
