---
title: Diseñador de la cinta de opciones (MFC)
ms.date: 11/19/2018
f1_keywords:
- vc.editors.ribbon.F1
helpviewer_keywords:
- Ribbon Designer (MFC)
- MFC Ribbon Designer
ms.assetid: 0806dfd6-7d11-471a-99e1-4072852231f9
ms.openlocfilehash: 1634eee30063a48041d60fc1b7116ca9543c9de2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511460"
---
# <a name="ribbon-designer-mfc"></a>Diseñador de la cinta de opciones (MFC)

El diseñador de la cinta de opciones permite crear y personalizar las cintas de opciones de las aplicaciones MFC. Una cinta de opciones es un elemento de la interfaz de usuario (IU) que organiza los comandos en grupos lógicos. Estos grupos aparecen en pestañas independientes en una banda a lo largo de la parte superior de la ventana. La cinta de opciones reemplaza a la barra de menús y a las barras de herramientas. Una cinta de opciones puede mejorar considerablemente la facilidad de uso de la aplicación. Para obtener más información, vea [cintas](/windows/win32/uxguide/cmd-ribbons)de opciones. En la siguiente ilustración se muestra una cinta de opciones.

![Control de recursos de la cinta de MFC](../mfc/media/ribbon_no_callouts.png "Control de recursos de la cinta de MFC")

En versiones anteriores de Visual Studio, las cintas debían crearse escribiendo código que utiliza las clases de la cinta de opciones de MFC como la [clase CMFCRibbonBar](../mfc/reference/cmfcribbonbar-class.md). En Visual Studio 2010 y versiones posteriores, el diseñador de la cinta de opciones proporciona un método alternativo para crear cintas de opciones. En primer lugar, cree y personalice una cinta de opciones como un recurso. A continuación, cargue el recurso de cinta de opciones desde el código en la aplicación MFC. Incluso puede usar los recursos de cinta de opciones y las clases de cinta de opciones MFC juntos. Por ejemplo, puede crear un recurso de cinta de opciones y, a continuación, agregarle mediante programación más elementos en tiempo de ejecución mediante código.

## <a name="understanding-the-ribbon-designer"></a>Descripción del diseñador de la cinta de opciones

El diseñador de la cinta de opciones crea y almacena la cinta de opciones como un recurso. Cuando se crea un recurso de cinta de opciones, el diseñador de la cinta de opciones hace estas tres cosas:

- Agrega una entrada en el script de definición de recursos de proyecto (*.rc). En el ejemplo siguiente, IDR_RIBBON es el nombre único que identifica el recurso de la cinta de opciones, RT_RIBBON_XML es el tipo de recurso y Ribbon. mfcribbon-MS es el nombre del archivo de recursos.

```
    IDR_RIBBON RT_RIBBON_XML      "res\\ribbon.mfcribbon-ms"
```

- Agrega las definiciones de identificadores de comando a resource.h.

```
#define IDR_RIBBON            307
```

- Crea un archivo de recursos de cinta de opciones (*.mfcribbon-ms) que contiene el código XML que define los botones, los controles y los atributos de la cinta de opciones. Los cambios realizados en la cinta de opciones en el diseñador de la cinta de opciones se almacenan en el archivo de recursos como XML. En el ejemplo de código siguiente se muestra parte del contenido \*de un archivo. mfcribbon-MS:

```
<RIBBON_BAR>
<ELEMENT_NAME>RibbonBar</ELEMENT_NAME>
<IMAGE>
<ID>
<NAME>IDB_BUTTONS</NAME>
<VALUE>113</VALUE>
</ID>
```

Para usar el recurso de la cinta de opciones en la aplicación MFC, cargue el recurso mediante una llamada a [CMFCRibbonBar:: LoadFromResource](../mfc/reference/cmfcribbonbar-class.md#loadfromresource).

## <a name="creating-a-ribbon-by-using-the-ribbon-designer"></a>Crear una cinta de opciones mediante el diseñador de la cinta de opciones

Estas son las dos maneras de agregar un recurso de cinta de opciones al proyecto MFC:

- Cree una aplicación MFC y configure el Asistente para proyectos MFC para crear la cinta de opciones. Para obtener más información, vea [Tutorial: Crear una aplicación de cinta mediante MFC](../mfc/walkthrough-creating-a-ribbon-application-by-using-mfc.md).

- En un proyecto MFC existente, cree un recurso de cinta de opciones y cárguelo. Para obtener más información, vea [Tutorial: Actualizar la aplicación Scribble de MFC (parte 1](../mfc/walkthrough-updating-the-mfc-scribble-application-part-1.md)).

Si el proyecto ya tiene una cinta de opciones codificada de forma manual, MFC tiene funciones que puede utilizar para convertir la cinta existente en un recurso de cinta de opciones. Para obtener más información, vea [Cómo: Convertir una cinta de MFC existente en un recurso](../mfc/how-to-convert-an-existing-mfc-ribbon-to-a-ribbon-resource.md)de la cinta de opciones.

> [!NOTE]
>  Las cintas de opciones no pueden crearse en aplicaciones basadas en cuadros de diálogo. Para obtener más información, vea [tipo de aplicación, Asistente para aplicaciones MFC](../mfc/reference/application-type-mfc-application-wizard.md).

## <a name="customizing-ribbons"></a>Personalizar cintas de opciones

Para abrir una cinta de opciones en el diseñador de la cinta de opciones, haga doble clic en el recurso de cinta de opciones en la vista de recursos. En el diseñador, puede agregar, quitar y personalizar elementos de la cinta de opciones, el botón Aplicación o la barra de herramientas de acceso rápido. También puede vincular eventos, por ejemplo, eventos de clic de botón y eventos de menú, a un método de la aplicación.

En la siguiente ilustración se muestran los distintos componentes del diseñador de la cinta de opciones.

![Diseñador de la cinta de MFC](../mfc/media/ribbon_designer.png "Diseñador de la cinta de MFC")

- **Herramientas** Contiene controles que se pueden arrastrar a la superficie del diseñador.

- **Superficie del diseñador:** Contiene la representación visual del recurso de la cinta de opciones.

- **Ventana Propiedades:** Muestra los atributos del elemento seleccionado en la superficie del diseñador.

- **Vista de recursos ventana:** Muestra los recursos que incluyen recursos de la cinta de opciones en el proyecto.

- **Barra de herramientas del editor de la cinta:** Contiene comandos que permiten obtener una vista previa de la cinta de opciones y cambiar su tema visual.

Los temas siguientes describen cómo usar las características del diseñador de la cinta de opciones:

- [Cómo: personalizar el botón Aplicación](../mfc/how-to-customize-the-application-button.md)

- [Cómo: personalizar la barra de herramientas de acceso rápido](../mfc/how-to-customize-the-quick-access-toolbar.md)

- [Cómo: agregar controles de cinta y controladores de eventos](../mfc/how-to-add-ribbon-controls-and-event-handlers.md)

- [Procedimientos: cargar un recurso de cinta desde una aplicación MFC](../mfc/how-to-load-a-ribbon-resource-from-an-mfc-application.md)

## <a name="definitions-of-ribbon-elements"></a>Definiciones de elementos de la cinta de opciones

![Cinta de MFC](../mfc/media/ribbon.png "Cinta de MFC")

- **Botón aplicación:** Botón que aparece en la esquina superior izquierda de una cinta de opciones. El botón Aplicación reemplaza al menú Archivo y está visible incluso cuando se minimiza la cinta de opciones. Al hacer clic en el botón, se muestra un menú con una lista de comandos.

- **Barra de herramientas de acceso rápido:** Una pequeña barra de herramientas personalizable que muestra comandos usados con frecuencia.

- **Categoría**: Agrupación lógica que representa el contenido de una pestaña de la cinta de opciones.

- **Botón predeterminado de categoría:** Botón que aparece en la cinta de opciones cuando se minimiza la cinta de opciones. Al hacer clic en el botón, la categoría vuelve a aparecer como un menú.

- **Plana** Área de la barra de cinta que muestra un grupo de controles relacionados. Cada categoría de la cinta de opciones contiene uno o más paneles de cinta de opciones.

- **Elementos de la cinta de opciones:** Controles de los paneles, por ejemplo, botones y cuadros combinados. Para ver los distintos controles que se pueden hospedar en una cinta de [opciones, vea ejemplo de RibbonGadgets: Aplicación](../overview/visual-cpp-samples.md)gadgets de la cinta de opciones.

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Trabajo con archivos de recursos](../windows/working-with-resource-files.md)
