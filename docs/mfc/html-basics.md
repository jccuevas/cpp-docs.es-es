---
title: "Conceptos básicos de HTML | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: HTML [MFC], about HTML
ms.assetid: aab8ea9f-12d4-4bdd-a585-ac3124081a2a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 852a4894478d139013d70813316976a20e99dd41
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="html-basics"></a>Conceptos básicos de HTML
Mayoría de los exploradores tiene la capacidad de examinar el código fuente HTML de las páginas que examina. Al ver el origen, verá un número de etiquetas HTML (lenguaje de marcado de hipertexto), incluido entre corchetes angulares (<>), entremezclados con texto.  
  
 Los pasos siguientes deberá usar etiquetas HTML para crear una página Web sencilla. En estos pasos, podrá escribir texto sin formato en un archivo en el Bloc de notas, realizar algunos cambios, guarde el archivo y vuelva a cargar la página en el explorador para ver los cambios.  
  
#### <a name="to-create-an-html-file"></a>Para crear un archivo HTML  
  
1.  Abra el Bloc de notas o en cualquier editor de texto sin formato.  
  
2.  Desde el **archivo** menú, elija `New`.  
  
3.  Escriba las líneas siguientes:  
  
 ```  
 <HTML>  
 <HEAD>  
 <TITLE>Top HTML Tags</TITLE>  
 </HEAD>  
 </HTML>  
 ```  
  
4.  Desde el **archivo** menú, elija **guardar**y guarde el archivo como c:\webpages\First.htm. Dejar el archivo abierto en el editor.  
  
5.  Conmutador en el explorador y desde el **archivo** menú, elija **abiertos**, o tipo `file://C:/webpages/first.htm` en el cuadro de edición de dirección URL del explorador. Debería ver una página en blanco con el título de ventana "Top HTML Tags."  
  
     Observe que las etiquetas están emparejadas y se incluyen entre corchetes angulares. Las etiquetas no distinguen mayúsculas de minúsculas y mayúsculas y minúsculas se usan a menudo para que destaquen mejor.  
  
     La etiqueta \<HTML > inicia el documento y la etiqueta \</HTML más externas > finaliza. Etiquetas de cierre (no siempre es necesarias) son los mismos que la etiqueta inicial, pero tienen una barra diagonal (/) delante de la etiqueta. No debería haber ningún espacio entre el corchete angular de cierre (<) y el inicio de la etiqueta.  
  
6.  Conmutador hacia el Bloc de notas y después de la  \< /HEAD > de línea, escriba:  
  
 ```  
 <BODY>  
    HTML is swell.  
    Life is good.  
 </BODY>  
 ```  
  
7.  Desde el **archivo** menú, elija **guardar**.  
  
8.  Volver al explorador y actualice la página.  
  
     Las palabras aparecerán en el área de cliente de la ventana del explorador. Tenga en cuenta que se omite el retorno de carro. Si desea tener un salto de línea, se debe incluir un `<BR>` después de la primera línea.  
  
     Para todos los pasos siguientes, inserte el texto en cualquier lugar entre \<cuerpo > y  \< /cuerpo > para agregar al cuerpo del documento.  
  
9. Agregar un encabezado:  
  
 ```  
 <H3>Here's the big picture</H3>  
 ```  
  
10. Agregar una imagen a partir de un archivo .gif guardado en el mismo directorio que la página:  
  
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
  
12. En la lista de números en su lugar, utilice emparejado \<OL > y \</OL > etiquetas en lugar de la \<UL > y \</UL > etiquetas.  
  
 Que debe ayudarle a comenzar. Si ve una característica excelente en una página Web, puede averiguar cómo se creó examinando el código fuente HTML. Editores de HTML como Microsoft FrontPage pueden utilizarse para crear páginas simples y avanzadas.  
  
 Este es el código fuente HTML completo para el archivo que ha sido creando:  
  
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
  
 Para obtener una descripción completa de etiquetas, atributos y extensiones, vea la especificación de lenguaje de marcado de hipertexto (HTML):  
  
 [http://www.w3.org/pub/www/MarkUp/](http://www.w3.org/pub/www/markup/)  
  
## <a name="see-also"></a>Vea también  
 [Fundamentos de programación para Internet de MFC](../mfc/mfc-internet-programming-basics.md)

