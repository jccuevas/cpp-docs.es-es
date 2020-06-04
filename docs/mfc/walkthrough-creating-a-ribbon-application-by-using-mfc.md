---
title: 'Tutorial: Crear una aplicación de cinta usando MFC'
ms.date: 09/09/2019
helpviewer_keywords:
- ribbon application, creating (MFC)
- creating a ribbon application (MFC)
ms.assetid: e61393e2-1d6b-4594-a7ce-157d3d1b0d9f
ms.openlocfilehash: 0f81b27d479b15864302b21a467bff9489ba465a
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821927"
---
# <a name="walkthrough-creating-a-ribbon-application-by-using-mfc"></a>Tutorial: Crear una aplicación de cinta usando MFC

En este tutorial se muestra cómo utilizar el **Asistente para aplicaciones MFC** para crear una aplicación que tenga una cinta de opciones de forma predeterminada. Después, puede expandir la cinta de opciones si agrega una categoría de cinta de opciones **personalizada** que tenga un panel de la cinta **Favoritos** y, a continuación, agregará algunos comandos usados con frecuencia al panel.

## <a name="prerequisites"></a>Requisitos previos

En este tutorial se supone que ha establecido Visual Studio para usar la **configuración de desarrollo general**. Si utiliza una configuración diferente, es posible que no se muestren algunos de los elementos de la interfaz de usuario a los que se hace referencia en las siguientes instrucciones.

### <a name="to-create-an-mfc-application-that-has-a-ribbon"></a>Para crear una aplicación MFC con una cinta de opciones

1. Utilice el **Asistente para aplicaciones MFC** para crear una aplicación MFC que tenga una cinta de opciones. Vea [Tutorial: usar los nuevos controles de Shell de MFC](walkthrough-using-the-new-mfc-shell-controls.md) para obtener instrucciones sobre cómo abrir el Asistente para su versión de Visual Studio.

1. Establezca las siguientes opciones en el **Asistente para aplicaciones MFC**:

    1. En la sección **tipo de aplicación** , en **estilo visual y colores**, seleccione **Office 2007 (tema azul)** .

    1. En la sección **compatibilidad con documentos compuestos** , asegúrese de que no está seleccionado **ninguno** .

    1. En la sección **propiedades de plantilla de documento** , en el cuadro extensión de **archivo** , escriba una extensión de nombre de archivo para los documentos que crea esta aplicación, por ejemplo, *mfcrbnapp*.

    1. En la sección **compatibilidad con bases de datos** (solo Visual Studio 2015), asegúrese de que no está seleccionado **ninguno** .

    1. En la sección características de la interfaz de usuario, asegúrese de que esté seleccionada **la opción usar una cinta** de **Opciones** .

    1. De forma predeterminada, el **Asistente para aplicaciones MFC** agrega compatibilidad con varios paneles de acoplamiento. Debido a que en este tutorial solo se enseña la cinta, puede quitar estas opciones de la aplicación. En la sección **características avanzadas** , desactive todas las opciones.

1. Haga clic en **Finalizar** para crear la aplicación MFC.

1. Para comprobar que la aplicación se creó correctamente, compílela y ejecútela. Para compilar la aplicación, en el menú **compilar** , haga clic en **compilar solución**. Si la aplicación se compila correctamente, haga clic en **iniciar depuración** en el menú **depurar** para ejecutarla.

    El asistente crea automáticamente una cinta de opciones que tiene una categoría de cinta denominada **Inicio**. Esta cinta de opciones contiene tres paneles de la cinta de opciones, que se denominan **portapapeles**, **vista**y **ventana**.

### <a name="to-add-a-category-and-panel-to-the-ribbon"></a>Para agregar una categoría y un panel a la cinta

1. Para abrir el recurso de la cinta de opciones que ha creado el asistente, en el menú **Ver** , seleccione **otras ventanas** y, a continuación, haga clic en **vista de recursos**. En **vista de recursos**, haga clic en **cinta** y, a continuación, haga doble clic en **IDR_RIBBON**.

1. En primer lugar, para agregar una categoría personalizada a la cinta de opciones, haga doble clic en **categoría** en el **cuadro de herramientas**.

    Se crea una categoría que tiene el título **Category1** . De forma predeterminada, la categoría contiene un panel.

    Haga clic con el botón secundario en **Category1** y después haga clic en **propiedades**. En la ventana **propiedades** , cambie **título** a *personalizado*.

    Las propiedades **grandes** imágenes e **imágenes pequeñas** especifican los mapas de bits que se usan como iconos para los elementos de la cinta de opciones de esta categoría. Dado que la creación de mapas de bits personalizados está fuera del ámbito de este tutorial, simplemente reutilice los mapas de bits creados por el asistente. Los mapas de bits pequeños son de 16 por 16 píxeles. En el caso de imágenes pequeñas, utilice los mapas de bits a los que tiene acceso el identificador de recurso de `IDB_FILESMALL`. Los mapas de bits grandes son de 32 por 32 píxeles. En el caso de imágenes grandes, utilice los mapas de bits a los que tiene acceso el identificador de recurso de `IDB_FILELARGE`.

    > [!NOTE]
    > En las pantallas HDPI (Gran número de puntos por pulgada), se usan automáticamente las versiones HDPI de las imágenes.

1. A continuación, personalice el panel. Los paneles se usan para agrupar los elementos que se relacionan lógicamente entre sí. Por ejemplo, en la pestaña **Inicio** de esta aplicación, los **comandos cortar**, **copiar**y **pegar** se encuentran en el panel **portapapeles** . Para personalizar el panel, haga clic con el botón secundario en **Panel1** y, a continuación, haga clic en **propiedades**. En la ventana **propiedades** , cambie **Caption** a *Favoritos*.

    Puede especificar el índice de la **imagen** para el panel. Este número especifica el icono que se muestra si el panel de la cinta de opciones se agrega a la **barra de herramientas de acceso rápido**. El icono no se muestra en el panel de la cinta de opciones.

1. Para comprobar que la categoría y el panel de la cinta se crearon correctamente, obtenga una vista previa del control de cinta. En la **barra de herramientas del editor**de la cinta, haga clic en el botón probar de la **cinta** . En la cinta de opciones se debe mostrar un panel **personalizado** de pestañas y **Favoritos** .

### <a name="to-add-elements-to-the-ribbon-panels"></a>Para agregar elementos a los paneles de la cinta

1. Para agregar elementos al panel que creó en el procedimiento anterior, arrastre los controles de la sección **Editor** de la cinta de opciones del **cuadro de herramientas** al panel en la vista de diseño.

1. En primer lugar, agregue un botón **Imprimir** . El botón **Imprimir** tendrá un submenú que contiene un comando de **impresión rápida** que imprime con la impresora predeterminada. Ambos comandos ya se han definido para esta aplicación. Están ubicados en el menú de la aplicación.

    Para crear el botón **Imprimir** , arrastre una herramienta de botón hasta el panel.

    En la ventana **propiedades** , cambie la propiedad **ID** por **ID_FILE_PRINT**, que ya debe estar definido. Cambie **Caption** a *Imprimir*. Cambie el índice de la **imagen** a *4*.

    Para crear el botón **impresión rápida** , haga clic en la columna valor de propiedad junto a **elementos de menú**y, a continuación, haga clic en los puntos suspensivos ( **...** ). En el **Editor de elementos**, haga clic en el botón **Agregar** sin etiquetar para crear un elemento de menú. En la ventana **propiedades** , cambie **Caption** a *impresión rápida*, **ID** a *ID_FILE_PRINT_DIRECT*e **Image** a *5*. La propiedad Image especifica el icono de **impresión rápida** en el `IDB_FILESMALL` recurso de mapa de bits.

1. Para comprobar que los botones se agregaron al panel de la cinta, compile la aplicación y ejecútela. Para compilar la aplicación, en el menú **compilar** , haga clic en **compilar solución**. Si la aplicación se compila correctamente, ejecute la aplicación haciendo clic en **iniciar depuración** en el menú **depurar** . Se deben mostrar el botón **Imprimir** y el cuadro combinado en el panel **Favoritos** de la pestaña **personalizada** de la cinta de opciones.

## <a name="next-steps"></a>Pasos siguientes

[Procedimiento para personalizar la barra de herramientas de acceso rápido](../mfc/how-to-customize-the-quick-access-toolbar.md)

[Procedimiento para personalizar el botón Aplicación](../mfc/how-to-customize-the-application-button.md)

Para obtener ejemplos de un extremo a otro, vea [ejemplos (MFC Feature Pack)](../overview/visual-cpp-samples.md).

## <a name="see-also"></a>Vea también

[Tutoriales](../mfc/walkthroughs-mfc.md)<br/>
[Ejemplos (MFC Feature Pack)](../overview/visual-cpp-samples.md)
