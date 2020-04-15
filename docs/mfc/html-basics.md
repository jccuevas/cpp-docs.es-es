---
title: Conceptos básicos de HTML
ms.date: 11/04/2016
helpviewer_keywords:
- HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
ms.openlocfilehash: 6d3a692eab47a1309ee0248b51ab8563fb077d5a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377246"
---
# <a name="html-basics"></a>Conceptos básicos de HTML

La mayoría de los navegadores tienen la capacidad de examinar el origen HTML de las páginas que navega. Cuando vea el origen, verá una serie de etiquetas HTML (lenguaje de marcado de hipertexto), rodeadas de corchetes angulares (<>), intercaladas con texto.

Los pasos siguientes utilizan etiquetas HTML para crear una página web sencilla. En estos pasos, escribirá texto sin formato en un archivo en el Bloc de notas, hará algunos cambios, guardará el archivo y volverá a cargar la página en el explorador para ver los cambios.

#### <a name="to-create-an-html-file"></a>Para crear un archivo HTML

1. Abra el Bloc de notas o cualquier editor de texto sin formato.

1. En el menú **Archivo,** elija **Nuevo**.

1. Escriba las siguientes líneas:

    ```html
    <HTML>
    <HEAD>
    <TITLE>Top HTML Tags</TITLE>
    </HEAD>
    </HTML>
    ```

1. En el menú **Archivo** , elija **Guardar**y guarde el archivo como c:-páginas web-First.htm. Deje el archivo abierto en el editor.

1. Cambie a su navegador y, en el menú **Archivo,** elija **Abrir**o escriba *file://C:/webpages/first.htm* en el cuadro de edición URL del explorador. Debería ver una página en blanco con el título de la ventana "Top HTML Tags."

   Observe que las etiquetas están emparejadas y se incluyen entre corchetes angulares. Las etiquetas no distinguen entre mayúsculas y minúsculas, pero las mayúsculas se utilizan a menudo para hacer que las etiquetas destaquen.

   La \<etiqueta HTML> inicia el \<documento y la etiqueta /HTML> lo finaliza. Las etiquetas finales (no siempre necesarias) son las mismas que la etiqueta inicial, pero tienen una barra diagonal (/) delante de la etiqueta. No debe haber espacios entre el corchete angular (<) y el inicio de la etiqueta.

1. Vuelva al Bloc de \<notas y, después de la línea de> /HEAD, escriba:

    ```html
    <BODY>
        HTML is swell.
        Life is good.
    </BODY>
    ```

1. En el menú **Archivo,** elija **Guardar**.

1. Vuelva a su navegador y actualice la página.

   Las palabras aparecerán en el área de cliente de la ventana de su navegador. Tenga en cuenta que se omite el retorno de carro. Si desea tener un salto de línea, debe incluir una `<BR>` etiqueta después de la primera línea.

   Para todos los pasos siguientes, \<inserte el \<texto en cualquier lugar entre> BODY y /BODY> para agregarlo al cuerpo del documento.

1. Agregue un encabezado:

    ```html
    <H3>Here's the big picture</H3>
    ```

1. Agregue una imagen, utilizando un archivo .gif guardado en el mismo directorio que su página:

    ```html
    <IMG src="yourfile.gif">
    ```

1. Agregue una lista:

    ```html
    <UL>Make me an unordered list.
    <LI>One programmer</LI>
    <LI>Ten SDKs</LI>
    <LI>Great Internet Apps</LI>
    </UL>
    ```

1. Para numerar la lista \<en su \<lugar, utilice etiquetas \<de> \<> OL emparejadas y /OL en lugar de las etiquetas> UL y /UL>.

Eso debería empezar. Si ve una gran característica en una página Web, puede averiguar cómo se creó examinando el origen HTML. Los editores HTML, como Microsoft Front Page, se pueden usar para crear páginas simples y avanzadas.

Aquí está todo el código fuente HTML para el archivo que ha estado creando:

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

Para obtener una descripción completa de etiquetas, atributos y extensiones, consulte la especificación de lenguaje de marcado de hipertexto (HTML):

[La última versión publicada de HTML](https://www.w3.org/TR/html/) en W3C.org.

## <a name="see-also"></a>Consulte también

[Fundamentos de programación de Internet de MFC](../mfc/mfc-internet-programming-basics.md)
