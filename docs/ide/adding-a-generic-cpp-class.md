---
title: Agregar una clase genérica de C++
ms.date: 11/09/2018
f1_keywords:
- vc.codewiz.classes.adding.generic
- vc.codewiz.class.generic
helpviewer_keywords:
- Visual C++, classes
- generic classes, adding
- generic classes
- generic C++ class wizard [C++]
ms.assetid: e95a5a14-dbed-4edc-8551-344fe48613cb
ms.openlocfilehash: 08ebe572da605e0f6d4d712bd7e48159598ba844
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/15/2018
ms.locfileid: "51694145"
---
# <a name="add-a-generic-c-class"></a>Agregar una clase genérica de C++

Se puede agregar una clase genérica de C++ mediante la **Vista de clases**. Una clase genérica de C++ es una clase que defina o que se deriva de una clase que defina.

**Para agregar una clase genérica de C++ a un proyecto:**

1. En la **Vista de clases**, haga clic con el botón derecho en el proyecto al que quiere agregar la clase nueva, elija **Agregar** y luego **Clase**.

1. En el cuadro de diálogo [Agregar clase](../ide/add-class-dialog-box.md), en el panel de plantillas, seleccione **Clase de C++**. Seleccione **Agregar** para mostrar el [Asistente de clases genéricas de C++](#generic-c-class-wizard).

1. En el asistente, proporcione un nombre de clase y, después, defina la configuración o acepte los valores predeterminados.

1. Para cerrar el asistente y ver la nueva clase genérica de C++ en el proyecto, seleccione **Finalizar**.

## <a name="in-this-section"></a>En esta sección

- [Asistente de clases genéricas de C++](#generic-c-class-wizard)

## <a name="generic-c-class-wizard"></a>Asistente de clases genéricas de C++

Agrega una clase genérica de C++ a un proyecto. La clase no hereda de ATL ni MFC.

- **Nombre de la clase**

  Establece el nombre de la clase nueva.

- **Archivo .h**

  Establece el nombre del archivo de encabezado para la clase nueva. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Para guardar el archivo de encabezado en la ubicación que prefiera, o para anexar la declaración de clase a un archivo existente, seleccione el botón de puntos suspensivos (**...**). Si especifica un archivo existente y selecciona **Finalizar**, el asistente le pide que especifique si se debe anexar la declaración de clase al contenido del archivo. Para anexar la declaración, seleccione **Sí**; para volver al asistente y especificar otro nombre de archivo, seleccione **No**.

- **Archivo .cpp**

  Establece el nombre del archivo de implementación para la clase nueva. De forma predeterminada, este nombre se basa en el que se proporcione en **Nombre de la clase**. Para guardar el archivo de implementación en la ubicación que prefiera, o para anexar la definición de clase a un archivo existente, seleccione el botón de puntos suspensivos (**...**). Si especifica un archivo existente y selecciona **Finalizar**, el asistente le pide que especifique si se debe anexar la definición de clase al contenido del archivo. Para anexar la definición, seleccione **Sí**; para volver al asistente y especificar otro nombre de archivo, seleccione **No**.

- **Clase base**

  Establece la clase base para la clase nueva.

- **Acceso**

  Establece el acceso a los miembros de clase base para la clase nueva. Los modificadores de acceso son palabras clave que especifican el nivel de acceso que tienen otras clases a las funciones miembro de la clase. Para obtener más información sobre cómo especificar el acceso, vea [Control de acceso a miembros](../cpp/member-access-control-cpp.md). De manera predeterminada, el nivel de acceso de la clase se establece en `public`.

  - `public`
  - `protected`
  - `private`
  - **Predeterminado** (no se genera ningún modificador de acceso).

- **Destructor virtual**

  Especifica si el destructor de clase es virtual. El uso de un destructor virtual ayuda a garantizar que se llama al destructor correcto cuando se eliminan instancias de clases derivadas.

- **Alineado**

  Genera el constructor de clase y la definición de clase como funciones alineadas en el archivo de encabezado.

- **Administrado**

  Cuando se selecciona, agrega una clase administrada y un archivo de encabezado. Cuando se desactiva, agrega una clase nativa y un archivo de encabezado.
