---
title: Conceptos básicos de HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 29ca2e3df4981db22a10281ba2a2938fc91d5b46
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620000"
---
# <a name="html-basics"></a>Conceptos básicos de HTML

La mayoría de los exploradores tienen la capacidad de examinar el origen HTML de las páginas que se examinan. Al ver el código fuente, verá una serie de etiquetas HTML (lenguaje de marcado de hipertexto), entre corchetes angulares (<>), entremezcladas con texto.

En los pasos siguientes se usan etiquetas HTML para compilar una página web sencilla. En estos pasos, escriba texto sin formato en un archivo en el Bloc de notas, realice algunos cambios, guarde el archivo y vuelva a cargar la página en el explorador para ver los cambios.

#### <a name="to-create-an-html-file"></a>Para crear un archivo HTML

1. Abra el Bloc de notas o cualquier editor de texto sin formato.

1. En el menú **archivo** , elija **nuevo**.

1. Escriba las líneas siguientes:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. En el menú **archivo** , elija **Guardar**y guarde el archivo como c:\webpages\First.htm. Deje abierto el archivo en el editor.

1. Cambie al explorador y, en el menú **archivo** , elija **abrir**o escriba *File://C:/Webpages/First.htm* en el cuadro de edición dirección URL del explorador. Debería ver una página en blanco con el título de la ventana "etiquetas HTML principales".

   Observe que las etiquetas se emparejan y se incluyen entre corchetes angulares. Las etiquetas no distinguen mayúsculas de minúsculas, pero a menudo se usa el uso de mayúsculas para hacer que las etiquetas destaquen.

   La etiqueta \<HTML> inicia el documento y la etiqueta \</HTML> lo termina. Las etiquetas de cierre (no siempre necesarias) son las mismas que las de la etiqueta de apertura, pero tienen una barra diagonal (/) delante de la etiqueta. No debe haber espacios entre el corchete angular (<) y el inicio de la etiqueta.

1. Vuelva al bloc de notas y, después de la \</HEAD> línea, escriba:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. En el menú **archivo** , elija **Guardar**.

1. Vuelva al explorador y actualice la página.

   Las palabras aparecerán en el área cliente de la ventana del explorador. Observe que se omite el retorno de carro. Si desea tener un salto de línea, debe incluir una `<BR>` etiqueta después de la primera línea.

   En todos los pasos que se indican a continuación, inserte el texto entre \<BODY> y \</BODY> para agregarlo al cuerpo del documento.

1. Agregue un encabezado:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Agregue una imagen mediante un archivo. gif guardado en el mismo directorio que la página:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Agregar una lista:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Para numerar la lista en su lugar, use \<OL> las etiquetas y emparejadas \</OL> en lugar de las \<UL> \</UL> etiquetas y.

Esto debería ayudarle a comenzar. Si ve una gran característica en una página web, puede averiguar cómo se creó examinando el código fuente HTML. Los editores HTML, como Microsoft Front Page, se pueden usar para crear páginas simples y avanzadas.

Este es el código fuente HTML completo del archivo que se ha creado:

```html
<HTML>
<HEAD>
<TITLE>Top HTML Tags</TITLE>
</HEAD>
<BODY>
HTML is swell.<BR>
Life is good.
<H3>Here's the big picture</H3>
<IMG src="yourfile.gif">
<UL>Make me an unordered list.
<LI>One programmer</LI>
<LI>Ten SDKs</LI>
<LI>Great Internet Apps</LI>
</UL>
</BODY>
</HTML>
```

Para obtener una descripción completa de etiquetas, atributos y extensiones, vea la especificación de Lenguaje de marcado de hipertexto (HTML):

[Última versión publicada de HTML](https://www.w3.org/TR/html/) en W3C.org.

## <a name="see-also"></a>Consulte también

[Fundamentos de la programación para Internet de MFC](mfc-internet-programming-basics.md)
