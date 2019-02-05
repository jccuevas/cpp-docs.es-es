---
title: Crear, mover y editar botones de barra de herramientas (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- buttons [C++], custom toolbars
- toolbar buttons [C++], editing
- buttons
- toolbar buttons [C++], creating
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
- toolbar buttons [C++], moving
- Toolbar editor [C++], moving buttons
- Toolbar editor [C++], copying buttons
- toolbars [C++], copying buttons
- toolbar buttons [C++], copying
- toolbar buttons [C++], deleting
- Toolbar editor [C++], deleting buttons
- Toolbar editor [C++], spacing toolbar buttons
- toolbar buttons [C++], space between buttons
- toolbar controls [MFC], command ID
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- command IDs, toolbar buttons
- size, toolbar buttons
- toolbar buttons [C++], setting properties
- Toolbar editor [C++], toolbar button properties
- status bars [C++], active toolbar button text
- command IDs, toolbar buttons
- width, toolbar buttons
ms.assetid: d0f0c6c6-9d7e-42b5-a86a-7558127386e7
ms.openlocfilehash: 2a67123e444ad208eaae74a24b72288f2dbb3bdb
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742705"
---
# <a name="creating-moving-and-editing-toolbar-buttons-c"></a>Crear, mover y editar botones de barra de herramientas (C++)

Puede crear fácilmente, mover, copiar y editar botones de la barra de herramientas.

De forma predeterminada, se muestra un botón nuevo o en blanco en el extremo derecho de la barra de herramientas. Puede mover este botón antes de editarlo. Cuando se crea un nuevo botón, aparece otro botón en blanco a la derecha del botón editado. Cuando se guarda una barra de herramientas, no se guarda el botón en blanco.

Las propiedades de un botón de barra de herramientas son:

|Property|Descripción|
|--------------|-----------------|
|**ID**|Define el identificador del botón. La lista desplegable proporciona comunes **ID** nombres.|
|**Width**|Establece el ancho del botón. se recomienda 16 píxeles.|
|**Height**|Establece el alto del botón. El alto de un botón cambia el alto de todos los botones de la barra de herramientas. se recomienda 15 píxeles.|
|**Preguntar**|Define el mensaje que se muestra en la barra de estado. Agregar un nombre y \n agrega una información sobre herramientas a ese botón de barra de herramientas. Para obtener más información, consulte [creación de una información sobre herramientas](../windows/creating-a-tool-tip-for-a-toolbar-button.md).|

**Ancho** y **alto** se aplican a todos los botones. Un mapa de bits que se usa para crear una barra de herramientas tiene un ancho máximo de 2048. Por lo que si se establece el ancho del botón en 512, solo puede tener cuatro botones y si se establece el ancho en 513, solo puede tener tres botones.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

Consulte las siguientes acciones:

## <a name="to-create-a-new-toolbar-button"></a>Para crear un nuevo botón de barra de herramientas

1. En [vista de recursos](../windows/resource-view-window.md) expanda la carpeta de recursos (por ejemplo, *Project1.rc*).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

1. Expanda el **barra de herramientas** carpeta y seleccione una barra de herramientas para editar.

1. Asignar un identificador al botón en blanco en el extremo derecho de la barra de herramientas. Puede hacerlo mediante la edición de la **ID** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window). Por ejemplo, desea dar a un botón de barra de herramientas en el mismo identificador que una opción de menú. En este caso, utilice el cuadro de lista desplegable para seleccionar el **ID** de la opción de menú.

   O bien

   Seleccione el botón en blanco en el extremo derecho de la barra de herramientas (en el **barra de herramientas Vista** panel) y empezar a dibujar. Se asigna un identificador de comando del botón predeterminado (ID\<n >).

También puede copiar y pegar una imagen en una barra de herramientas como un botón nuevo.

## <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>Para agregar una imagen a una barra de herramientas como un botón

1. En [vista de recursos](../windows/resource-view-window.md), abra la barra de herramientas haciendo doble clic en él.

1. A continuación, abra la imagen que le gustaría agregar a la barra de herramientas.

   > [!NOTE]
   > Si la imagen se abre en Visual Studio, se abrirá en el **imagen** editor. También puede abrir la imagen en otros programas de gráficos.

1. Desde el **editar** menú, elija **copia**.

1. Cambiar a la barra de herramientas seleccionando su pestaña de la parte superior de la ventana de código fuente.

1. Desde el **editar** menú, elija **pegar**.

   La imagen aparecerá en la barra de herramientas como un botón nuevo.

## <a name="to-move-a-toolbar-button"></a>Para mover un botón de barra de herramientas

En el **barra de herramientas Vista** panel, arrastre el botón que desea mover a su nueva ubicación en la barra de herramientas.

## <a name="to-copy-buttons-from-a-toolbar"></a>Copiar botones de una barra de herramientas

1. Mantenga presionada la **Ctrl** clave.

1. En el **barra de herramientas Vista** panel, arrastre el botón a su nueva ubicación en la barra de herramientas o en una ubicación en otra barra de herramientas.

## <a name="to-delete-a-toolbar-button"></a>Para eliminar un botón de barra de herramientas

Seleccione el botón de barra de herramientas y arrástrela fuera de la barra de herramientas.

## <a name="to-insert-or-remove-space-between-buttons-on-a-toolbar"></a>Para insertar o quitar espacio entre los botones de una barra de herramientas

En general, para insertar un espacio entre los botones, arrástrelos fuera de ellas en la barra de herramientas. Para quitar espacio, arrástrelos hacia entre sí.

### <a name="to-insert-a-space-before-a-button-that-isnt-followed-by-a-space"></a>Para insertar un espacio delante de un botón que no está seguido por un espacio

Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-to-keep-the-trailing-space"></a>Para insertar un espacio delante de un botón que va seguido de un espacio y mantener el espacio final

Arrastre el botón hasta que el borde derecho o inferior, simplemente es tocar el botón siguiente o se superpone a él.

### <a name="to-insert-a-space-before-a-button-that-is-followed-by-a-space-and-close-up-that-following-space"></a>Para insertar un espacio delante de un botón que va seguido de un espacio y cerrar espacio siguiente

Arrastre el botón a la derecha o hacia abajo hasta que se superpone sobre el botón siguiente acerca de la mitad.

### <a name="to-remove-a-space-between-buttons-on-a-toolbar"></a>Para quitar un espacio entre los botones de una barra de herramientas

Arrastre el botón en un lado del espacio hacia el botón del otro lado del espacio hasta que se superponga con el botón siguiente aproximadamente hasta la mitad.

   Si no hay ningún espacio en el lado del botón que arrastra fuera del, y arrastra el botón más de la mitad pasado el botón adyacente, el **barra de herramientas** editor también inserta un espacio en el lado opuesto del botón que le operación de arrastre.

## <a name="to-change-the-properties-of-a-toolbar-button"></a>Para cambiar las propiedades de un botón de barra de herramientas

1. En un proyecto de C++, seleccione el botón de barra de herramientas.

1. Escriba el nuevo identificador en el **ID** propiedad en el [ventana propiedades](/visualstudio/ide/reference/properties-window), o use la lista desplegable para seleccionar un nuevo **ID**.

## <a name="requirements"></a>Requisitos

MFC o ATL

## <a name="see-also"></a>Vea también

[Editor de barras de herramientas](../windows/toolbar-editor.md)
