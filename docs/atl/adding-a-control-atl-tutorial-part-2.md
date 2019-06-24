---
title: Agregar un control (Tutorial de ATL, Parte 2)
ms.custom: get-started-article
ms.date: 09/26/2018
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: 53f38d63a44328bf014f04635a24989a875ddf1e
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344325"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Agregar un control (Tutorial de ATL, Parte 2)

En este paso, agregue un control a su proyecto, compilarlo y probarlo en una página Web.

## <a name="procedures"></a>Procedimientos

### <a name="to-add-an-object-to-an-atl-project"></a>Para agregar un objeto a un proyecto ATL

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto `Polygon`.

1. Seleccione **agregar** en el menú contextual y haga clic en **nuevo elemento** en el submenú.

    Aparecerá el cuadro de diálogo **Agregar nuevo elemento**. Las distintas categorías de objetos se enumeran en la estructura de árbol a la izquierda.

1. Haga clic en el **ATL** carpeta.

1. En la lista de plantillas de la derecha, seleccione **Control ATL**. Haga clic en **Agregar**. El **Control ATL** asistente abrirá y se puede configurar el control.

1. Tipo `PolyCtl` como el nombre corto y tenga en cuenta que los demás campos se completan automáticamente. No haga clic en **finalizar** aún, ya que debe realizar algunos cambios más.

El **Control ATL** del asistente **nombres** página contiene los siguientes campos:

|Campo|Contenido|
|-----------|--------------|
|**Nombre corto**|El nombre que especificó para el control.|
|**Clase**|El nombre de la clase de C++ creada para implementar el control.|
|**Archivo .h**|El archivo creado para contener la definición de la clase de C++.|
|**Archivo .cpp**|El archivo creado para contener la implementación de la clase de C++.|
|**CoClass**|Nombre de la clase de componente para este control.|
|**Interface**|El nombre de la interfaz donde el control implementará sus métodos y propiedades personalizados.|
|**Type**|Una descripción del control.|
|**ProgID**|El nombre legible que se puede utilizar para buscar el CLSID del control.|

Encontrará varias configuraciones adicionales que deben cambiarse en el **Control ATL** asistente.

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Para habilitar la compatibilidad con la información de error enriquecida y con los puntos de conexión

1. Haga clic en **opciones** para abrir el **opciones** página.

1. Seleccione el **puntos de conexión** casilla de verificación. Esta opción crea el soporte técnico para una interfaz de salida en el archivo IDL.

También puede agregar las interfaces para ampliar la funcionalidad del control.

### <a name="to-extend-the-controls-functionality"></a>Para ampliar la funcionalidad del control

1. Haga clic en **Interfaces** para abrir el **Interfaces** página.

1. Seleccione `IProvideClassInfo2` y haga clic en el **seguridad** flecha para moverla a la **admitidos** lista.

1. Seleccione `ISpecifyPropertyPages` y haga clic en el **seguridad** flecha para moverla a la **admitidos** lista.

También puede hacer que el control *insertable*, lo que significa que es puede insertarse en las aplicaciones que admiten objetos incrustados, como Excel o Word.

### <a name="to-make-the-control-insertable"></a>Para que el control se pueda insertar

1. Haga clic en **apariencia** para abrir el **apariencia** página.

1. Seleccione el **Insertable** casilla de verificación.

El polígono mostrado por el objeto tendrá un color de relleno sólido, por lo que debe agregar una propiedad estándar `Fill Color`.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Para agregar una propiedad estándar Color de relleno y crear el control

1. Haga clic en **propiedades estándar** para abrir el **propiedades estándar** página.

1. En **no admite**, desplácese hacia abajo en la lista de propiedades estándar posibles. Seleccione `Fill Color` y haga clic en el **seguridad** flecha para moverla a la **admitidos** lista.

1. Elija **Finalizar**.

Mientras el asistente crea el control, se producen varios cambios de código y adiciones de archivos. Se crean los siguientes archivos:

|Archivo|Descripción|
|----------|-----------------|
|PolyCtl.h|Contiene la mayor parte de la implementación de la clase `CPolyCtl` de C++.|
|PolyCtl.cpp|Contiene los elementos restantes de `CPolyCtl`.|
|PolyCtl.rgs|Un archivo de texto que contiene el script del Registro utilizado para registrar el control.|
|PolyCtl.htm|Una página web que contiene una referencia al control recién creado.|

El asistente también realiza los cambios de código siguiente:

- Agrega un `#include` archivos necesario para admitir controles de instrucción a los archivos stdafx.h y stdafx.cpp para incluir la biblioteca ATL.

- Cambia Polygon.idl para incluir detalles del nuevo control.

- Agrega el nuevo control al mapa de objetos en Polygon.cpp.

Ahora puede compilar el control para verlo en acción.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control

1. En el **compilar** menú, haga clic en **compilar polígono**.

    Una vez que termina la compilación de control, haga clic en PolyCtl.htm en **el Explorador de soluciones** y seleccione **ver en el explorador**. Se muestra la página HTML Web que contiene el control. Debería ver una página con el título "ATL 8.0 página de prueba para el objeto PolyCtl" y su control, el texto PolyCtl.

> [!NOTE]
> Si el control no está visible, sabe que algunos exploradores necesitan ajustes de configuración para ejecutar los controles ActiveX. Consulte la documentación del explorador sobre cómo habilitar los controles ActiveX.

> [!NOTE]
> Al completar este tutorial, si recibe un mensaje de error que no se puede crear el archivo DLL, cierre el archivo PolyCtl.htm y ActiveX Control Test container y compile la solución de nuevo. Si todavía no se puede crear el archivo DLL, reinicie el equipo o cerrar la sesión si usa servicios de Terminal Server.

A continuación, agregará una propiedad personalizada al control.

[Vuelva al paso 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [con el paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
