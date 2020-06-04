---
title: Agregar una página de propiedades (Tutorial de ATL, Parte 6)
ms.custom: get-started-article
ms.date: 09/27/2018
ms.assetid: df80d255-e7ea-49d9-b940-3f012e90cf9b
ms.openlocfilehash: 467ae19c372e24b2d368002cb83367b7087136fd
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078768"
---
# <a name="adding-a-property-page-atl-tutorial-part-6"></a>Agregar una página de propiedades (Tutorial de ATL, Parte 6)

> [!NOTE]
> El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

Las páginas de propiedades se implementan como objetos COM independientes, lo que permite compartirlas si es necesario. En este paso, realizará las tareas siguientes para agregar una página de propiedades al control:

- Crear el recurso de página de propiedades

- Agregar código para crear y administrar la página de propiedades

- Agregar la página de propiedades al Control

## <a name="creating-the-property-page-resource"></a>Crear el recurso de página de propiedades

Para agregar una página de propiedades al control, use la plantilla de página de propiedades ATL.

### <a name="to-add-a-property-page"></a>Agregar una página de propiedades

1. En el **Explorador de soluciones**, haga clic con el botón derecho en `Polygon`.

1. En el menú contextual, haga clic en **Agregar** > **Nuevo elemento**.

1. En la lista de plantillas, seleccione **ATL** > **Página de propiedades ATL** y haga clic en **Agregar**.

1. Cuando el **Asistente para páginas de propiedades ATL** aparece, escriba *PolyProp* como nombre **corto**.

1. Haga clic en **Cadenas** para abrir la página **Cadenas** y escriba **&Polígono** como **título**.

   El **título** de la página de propiedades es la cadena que aparece en la pestaña de esa página. La **cadena de documento** es una descripción que usa un marco de propiedades para colocar una sugerencia de línea o información sobre herramientas. Tenga en cuenta que el marco de propiedades estándar actualmente no usa esta cadena, por lo que puede conservar el contenido predeterminado. No se generará un **archivo de ayuda** en este momento, así que elimine la entrada en ese cuadro de texto.

1. Haga clic en **Finalizar**; se creará el objeto de la página de propiedades.

Se crean los tres archivos siguientes:

|Archivo|Descripción|
|----------|-----------------|
|PolyProp.h|Contiene la clase C++ `CPolyProp`, que implementa la página de propiedades.|
|PolyProp.cpp|Incluye el archivo PolyProp.h.|
|PolyProp.rgs|El script de registro que registra el objeto de la página de propiedades.|

Los cambios siguientes de código también son posibles:

- La página de propiedades nueva se agrega a la asignación de entrada de objetos en Polygon.cpp.

- La clase `PolyProp` se agrega al archivo Polygon.idl.

- El nuevo archivo de script de registro PolyProp.rgs se agrega a los recursos del proyecto.

- Una plantilla de cuadro de diálogo se agrega a los recursos del proyecto de la página de propiedades.

- Las cadenas de propiedades que ha especificado se agregan a la tabla de cadenas de recursos.

Ahora agregue los campos que desea que aparezcan en la página de propiedades.

### <a name="to-add-fields-to-the-property-page"></a>Agregar campos a la página de propiedades

1. En el **Explorador de soluciones**, haga doble clic en el archivo de recursos Polygon.rc. Se abrirá **Vista de recursos**.

1. En **Vista de recursos**, expanda el nodo `Dialog` y haga doble clic en `IDD_POLYPROP`. Tenga en cuenta que el cuadro de diálogo que aparece se muestra vacío, salvo por una etiqueta que indica si debe inserte aquí los controles.

1. Seleccione esa etiqueta y cámbiela a `Sides:` de lectura modificando el texto **Título** de la ventana **Propiedades**.

1. Cambie el tamaño del cuadro de etiqueta para que se ajuste el tamaño del texto.

1. Arrastre un **control Edit** desde el **cuadro de herramientas** a la derecha de la etiqueta.

1. Por último, cambie el **identificador** de control de edición a `IDC_SIDES` utilizando la ventana **Propiedades**.

Este paso completa el proceso de crear el recurso de página de propiedades.

## <a name="adding-code-to-create-and-manage-the-property-page"></a>Agregar código para crear y administrar la página de propiedades

Ahora que ha creado el recurso de página de propiedades, tiene que escribir el código de implementación.

En primer lugar, habilite la clase `CPolyProp` para establecer el número de lados en el objeto cuando se pulse el botón **Aplicar**.

### <a name="to-modify-the-apply-function-to-set-the-number-of-sides"></a>Modificar la función Aplicar para establecer el número de lados

1. Reemplace la función `Apply` en PolyProp.h por el código siguiente:

    [!code-cpp[NVC_ATL_Windowing#58](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_1.h)]

Una página de propiedades puede tener más de un cliente asociado en cualquier momento, por lo que la función `Apply` reinicia el bucle y llama a `put_Sides` en cada cliente con el valor recuperado el cuadro de edición. Está usando la clase [CComQIPtr](../atl/reference/ccomqiptr-class.md), que lleva a cabo la operación `QueryInterface` en cada objeto para obtener la interfaz `IPolyCtl` de la interfaz `IUnknown` (almacenada en la matriz `m_ppUnk`).

Ahora, el código comprueba que la propiedad `Sides` realmente funcione. Si se produce un error, el código muestra un cuadro de mensaje con los detalles del error de la interfaz `IErrorInfo`. Normalmente, un contenedor solicita un objeto para la interfaz `ISupportErrorInfo` y llama a `InterfaceSupportsErrorInfo` primero, para determinar si el objeto admite la información de error de configuración. Puede omitir esta tarea.

[CComPtr](../atl/reference/ccomptr-class.md) lo ayuda a controlar automáticamente el recuento de referencias, por lo que no es necesario llamar a `Release` en la interfaz. `CComBSTR` lo ayuda con el procesamiento de BSTR, por lo que no es necesario que realizar la llamada a `SysFreeString` final. También usa una de las diferentes clases de conversión de cadenas, por lo que puede convertir BSTR si es necesario (motivo por el cual la macro USES_CONVERSION se encuentra al principio de la función).

También deberá establecer la marca de modificado de la página de propiedades para indicar que el botón **Aplicar** debe estar habilitado. Esto se produce cuando el usuario cambia el valor en el cuadro de texto **Lados**.

### <a name="to-handle-the-apply-button"></a>Controlar el botón Aplicar

1. En **Vista de clases**, haga clic en el botón derecho en `CPolyProp` y en **Propiedades** en el menú contextual.

1. En la ventana **Propiedades**, haga clic en la pestaña **Eventos**.

1. Expanda el nodo `IDC_SIDES` en la lista de eventos.

1. Seleccione `EN_CHANGE` y en el menú desplegable a la derecha, haga clic en **\<Agregar>OnEnChangeSides**. La declaración del controlador `OnEnChangeSides` se agregará a Polyprop.h y la implementación del controlador a Polyprop.cpp.

A continuación, modificará el controlador.

### <a name="to-modify-the-onenchangesides-method"></a>Modificar el método OnEnChangeSides

1. Agregue el código siguiente en Polyprop.cpp al método `OnEnChangeSides` (eliminando cualquier código que el Asistente coloque allí):

    [!code-cpp[NVC_ATL_Windowing#59](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_2.cpp)]

Se llamará a `OnEnChangeSides` cuando se envía un mensaje `WM_COMMAND` con la notificación `EN_CHANGE` para el control `IDC_SIDES`. `OnEnChangeSides` a continuación llama a `SetDirty` y pasa TRUE para indicar que la página de propiedades ahora está modificada y el botón **Aplicar** debe estar habilitado.

## <a name="adding-the-property-page-to-the-control"></a>Agregar la página de propiedades al Control

La plantilla de página de propiedades ATL y el asistente no agregan la página de propiedades al control automáticamente, ya que podría haber varios controles en el proyecto. Deberá agregar una entrada a la asignación de propiedades del control.

### <a name="to-add-the-property-page"></a>Agregar la página de propiedades

1. Abra PolyCtl.h y agregue estas líneas a la asignación de propiedades:

    [!code-cpp[NVC_ATL_Windowing#60](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_3.h)]

La asignación de propiedad del control ahora tendrá este aspecto:

[!code-cpp[NVC_ATL_Windowing#61](../atl/codesnippet/cpp/adding-a-property-page-atl-tutorial-part-6_4.h)]

Podría haber agregado una macro `PROP_PAGE` con el identificador CLSID de la página de propiedades, pero si utiliza la macro `PROP_ENTRY` tal como se muestra, el valor de propiedad `Sides` también se guarda cuando se guarda el control.

Los tres parámetros de la macro son la descripción de la propiedad, el identificador DISPID de la propiedad y el identificador CLSID de la página de propiedades que tiene la propiedad. Esto es útil si, por ejemplo, carga el control en Visual Basic y establece el número de lados en el tiempo de diseño. Como el número de lados se guarda, al volver a cargar el proyecto de Visual Basic, se restaurará el número de lados.

## <a name="building-and-testing-the-control"></a>Compilar y probar el control

Ahora, genere el control e insértelo en ActiveX Control Test Container. En **Test Container**, en el menú **Editar**, haga clic en **Objeto de la clase de PolyCtl**. Aparece la página de propiedades con la información que agregó.

El botón **Aplicar** está deshabilitado inicialmente. Comience a escribir un valor en el cuadro **Lados** y el botón **Aplicar** se habilitará. Cuando haya terminado de escribir el valor, haga clic en el botón **Aplicar**. La visualización del control cambia y el botón **Aplicar** se deshabilita de nuevo. Pruebe a escribir un valor no válido. Verá un cuadro de mensaje que contiene la descripción del error que establece desde la función `put_Sides`.

A continuación, colocará el control en una página web.

[Volver al paso 5](../atl/adding-an-event-atl-tutorial-part-5.md) &#124; [Avanzar al paso 7](../atl/putting-the-control-on-a-web-page-atl-tutorial-part-7.md)

## <a name="see-also"></a>Consulte también

[Tutorial](../atl/active-template-library-atl-tutorial.md)
