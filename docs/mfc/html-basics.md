---
title: "Conceptos b&#225;sicos de HTML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "HTML, acerca de HTML"
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
caps.latest.revision: 7
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Conceptos b&#225;sicos de HTML
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La mayoría de los exploradores tienen la capacidad de examinar el código fuente HTML de las páginas que se examina.  Cuando se ve el origen que verá varias etiquetas HTML \(lenguaje de marcación de hipertexto\), delimitadas por corchetes angulares \(\<\>\), están intercalados con el texto.  
  
 Los pasos bajo las etiquetas HTML de uso para compilar una página Web sencilla.  En estos pasos, escribirá el texto sin formato de un archivo en el Bloc de notas, realizará algunos cambios, guarde el archivo, y recargará la página en el explorador para ver los cambios.  
  
#### Para crear un archivo HTML  
  
1.  Abra Bloc de notas o cualquier editor de texto sin formato.  
  
2.  En el menú de **archivo** , elija `New`.  
  
3.  Escriba las líneas siguientes:  
  
    ```  
    <HTML>  
    <HEAD>  
    <TITLE>Top HTML Tags</TITLE>  
    </HEAD>  
    </HTML>  
    ```  
  
4.  En el menú de **archivo** , elija **Guardar**, y guarde el archivo como c:\\webpages\\First.htm.  Deje abierto el archivo en el editor.  
  
5.  Cambie al explorador y, en el menú de **archivo** , elija **Abierta**, o escriba `file://C:/webpages/first.htm` en el cuadro de edición de la dirección URL del explorador.  Debe ver una página en blanco con la ventana generación “etiquetas HTML máximas.”  
  
     Observe las etiquetas están emparejadas y se incluyen entre corchetes angulares.  Las etiquetas no distinguen entre mayúsculas y minúsculas, pero el uso de mayúsculas suele usarse para crear que las etiquetas se resaltan.  
  
     La etiqueta \<HTML\> comienza el documento, y label \/HTML \<\> end.  Finalizando las etiquetas \(necesarias no siempre\) es igual que la etiqueta inicial, pero tiene una barra diagonal \(\/\) delante de la etiqueta.  No puede haber espacios entre el corchete angular \(\<\) y el inicio de la etiqueta.  
  
6.  Vuelva al Bloc de notas, y después \<de la\> línea de \/HEAD, escriba:  
  
    ```  
    <BODY>  
    HTML is swell.  
    Life is good.  
    </BODY>  
    ```  
  
7.  En el menú de **archivo** , elija **Guardar**.  
  
8.  Vuelva al explorador y actualizan la página.  
  
     Las palabras aparecerán en el área de cliente de la ventana del explorador.  Observe que el retorno de carro se omite.  Si desea tener un salto de línea, debe incluir una etiqueta de `<BR>` después de la primera línea.  
  
     Para todos los pasos siguientes, insertar el texto en cualquier parte entre \<el CUERPO\> y \<\/BODY\> para agregar el cuerpo del documento.  
  
9. Agregue un encabezado:  
  
    ```  
    <H3>Here's the big picture</H3>  
    ```  
  
10. Agregue una imagen, mediante un archivo .gif guardado en el mismo directorio que la página:  
  
    ```  
    <IMG src="yourfile.gif">  
    ```  
  
11. Agregue una lista:  
  
    ```  
    <UL>Make me an unordered list.  
    <LI>One programmer</LI>  
    <LI>Ten SDKs</LI>  
    <LI>Great Internet Apps</LI>  
    </UL>  
    ```  
  
12. El número la lista en su lugar, utiliza OL\> emparejado \<y \<\/OL\> etiqueta en \<su lugar UL\> y \<etiquetas\> de \/UL.  
  
 Esto debe comenzar.  Si ve grandes característica en una página Web, puede averiguar cómo se creó examinando el código fuente HTML.  Los editores HTML como portada de Microsoft se pueden utilizar para crear páginas simples y avanzado.  
  
 A continuación se muestra el código fuente HTML completo del archivo que ha estado compilar:  
  
```  
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
  
 Para obtener una descripción completa de etiquetas, los atributos, y las extensiones, vea la especificación del Lenguaje de marcado de hipertexto \(HTML\):  
  
 [http:\/\/www.w3.org\/pub\/WWW\/MarkUp\/](http://www.w3.org/pub/WWW/MarkUp/)  
  
## Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)