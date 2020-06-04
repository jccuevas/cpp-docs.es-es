---
title: Agregar un control (Tutorial de ATL, Parte 2)
ms.custom: get-started-article
ms.date: 08/19/2019
ms.assetid: c9575a75-1064-41f1-9697-7aada560c669
ms.openlocfilehash: b7952f42b24c4211a2c44ea71fd17e4f65c3421a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630711"
---
# <a name="adding-a-control-atl-tutorial-part-2"></a>Agregar un control (Tutorial de ATL, Parte 2)

En este paso, agregará un control al proyecto, lo compilará y lo probará en una página web.

## <a name="procedures"></a>Procedimientos

### <a name="to-add-an-object-to-an-atl-project"></a>Para agregar un objeto a un proyecto ATL

1. En el **Explorador de soluciones**, haga clic con el botón derecho en el proyecto `Polygon`.

1. Seleccione **Agregar** en el menú contextual y haga clic en **nuevo elemento** en el submenú.

    Aparecerá el cuadro de diálogo **Agregar nuevo elemento**. Las distintas categorías de objetos se enumeran en la estructura de árbol a la izquierda.

1. Haga clic en la carpeta **ATL** .

1. En la lista de plantillas de la derecha, seleccione **control ATL**. Haga clic en **Agregar**. Se abrirá el Asistente para **controles ATL** y podrá configurar el control.

1. Escriba `PolyCtl` como nombre corto y observe que los demás campos se completan automáticamente. No haga clic en **Finalizar** todavía, porque debe realizar algunos cambios más.

La página **nombres** del Asistente para **controles ATL** contiene los siguientes campos:

|Campo|Contenido|
|-----------|--------------|
|**Nombre corto**|El nombre que especificó para el control.|
|**Clase**|El nombre de la clase de C++ creada para implementar el control.|
|**Archivo .h**|El archivo creado para contener la definición de la clase de C++.|
|**Archivo .cpp**|El archivo creado para contener la implementación de la clase de C++.|
|**Coclase**|Nombre de la clase de componente para este control.|
|**Interface**|El nombre de la interfaz donde el control implementará sus métodos y propiedades personalizados.|
|**Type**|Una descripción del control.|
|**ProgID**|El nombre legible que se puede utilizar para buscar el CLSID del control.|

En el Asistente para **controles ATL** , se deben cambiar varias opciones de configuración adicionales.

### <a name="to-enable-support-for-rich-error-information-and-connection-points"></a>Para habilitar la compatibilidad con la información de error enriquecida y con los puntos de conexión

1. Haga clic en **Opciones** para abrir la página **Opciones** .

1. Active la casilla **puntos de conexión** . Esta opción permite crear una interfaz de salida en el archivo IDL.

También puede Agregar interfaces para extender la funcionalidad del control.

### <a name="to-extend-the-controls-functionality"></a>Para extender la funcionalidad del control

1. Haga clic en **interfaces** para abrir la página **interfaces** .

1. Seleccione `IProvideClassInfo2` y haga clic en la flecha **arriba** para moverla a la lista admitida.

1. Seleccione `ISpecifyPropertyPages` y haga clic en la flecha **arriba** para moverla a la lista admitida.

También puede hacer que el control se pueda *Insertar*, lo que significa que se puede incrustar en aplicaciones que admiten objetos incrustados, como Excel o Word.

### <a name="to-make-the-control-insertable"></a>Para que el control se pueda insertar

1. Haga clic en **apariencia** para abrir la página **apariencia** .

1. Active la casilla insertable.

El polígono mostrado por el objeto tendrá un color de relleno sólido, por lo que debe agregar una propiedad estándar `Fill Color`.

### <a name="to-add-a-fill-color-stock-property-and-create-the-control"></a>Para agregar una propiedad estándar Color de relleno y crear el control

1. Haga clic en **propiedades estándar** para abrir la página **propiedades estándar** .

1. En **no compatible**, desplácese hacia abajo en la lista de propiedades estándar posibles. Seleccione `Fill Color` y haga clic en la flecha **arriba** para moverla a la lista admitida.

1. Elija **Finalizar**.

Cuando el asistente crea el control, se producen varios cambios de código y adiciones de archivos. Se crean los siguientes archivos:

|Archivo|DESCRIPCIÓN|
|----------|-----------------|
|PolyCtl.h|Contiene la mayor parte de la implementación de la clase `CPolyCtl` de C++.|
|PolyCtl.cpp|Contiene los elementos restantes de `CPolyCtl`.|
|PolyCtl.rgs|Un archivo de texto que contiene el script del Registro utilizado para registrar el control.|
|PolyCtl.htm|Una página web que contiene una referencia al control recién creado.|

El Asistente también realiza los siguientes cambios en el código:

- Agrega una `#include` instrucción a los archivos de encabezado precompilados para incluir los archivos ATL necesarios para admitir controles.

- Cambia Polygon. idl para incluir detalles del nuevo control.

- Agrega el nuevo control al mapa de objetos en Polygon. cpp.

Ahora puede compilar el control para verlo en acción.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

### <a name="to-build-and-test-the-control"></a>Para compilar y probar el control

1. En el menú compilar, haga clic en compilar **polígono**.

    Una vez que el control termine de compilar, haga clic con el botón secundario en PolyCtl. htm en **Explorador de soluciones** y seleccione **ver en el explorador**. Se muestra la página web HTML que contiene el control. Debería ver una página con el título "página de prueba de ATL 8,0 para el objeto PolyCtl" y el control, el texto PolyCtl.

> [!NOTE]
> Si el control no está visible, sepa que algunos exploradores requieren ajustes de configuración para ejecutar controles ActiveX. Consulte la documentación del explorador sobre cómo habilitar los controles ActiveX.

> [!NOTE]
> Al completar este tutorial, si recibe un mensaje de error que indica que no se puede crear el archivo DLL, cierre el archivo PolyCtl. htm y ActiveX Control Test Container y vuelva a compilar la solución. Si sigue sin poder crear el archivo DLL, reinicie el equipo o cierre la sesión si usa Terminal Services.

A continuación, agregará una propiedad personalizada al control.

[Volver al paso 1](../atl/creating-the-project-atl-tutorial-part-1.md) &#124; [En el paso 3](../atl/adding-a-property-to-the-control-atl-tutorial-part-3.md)

## <a name="see-also"></a>Vea también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
